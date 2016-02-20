#ARCH=ARM
MY_LIB_PATH=/home/gnu_src

ifeq ($(ARCH),ARM)
#CROSS=arm-linux-
CROSS=mipsel-openwrt-linux-
endif

SRC:=$(shell ls *.c)
SRC+=$(shell ls *.cpp)

#CFLAG:=-DMEMWATCH -DMW_STDIO
#LDFLAG:=-static

ifeq ($(ARCH),ARM)
#IPATH:=-I$(MY_LIB_PATH)/sqlite-3.7.3/output/arm/include
IPATH:=-I./libconfig-x86-64/include
else
#IPATH:=-I$(MY_LIB_PATH)/sqlite-3.7.3/output/ubuntu/include
IPATH:=-I./libconfig-x86-64/include
endif

ifeq ($(ARCH),ARM)
#LPATH:=-L$(MY_LIB_PATH)/sqlite-3.7.3/output/arm/lib
LPATH:=-L./libconfig-x86-64/lib
else
#LPATH:=-L$(MY_LIB_PATH)/sqlite-3.7.3/output/ubuntu/lib
LPATH:=-L./libconfig-x86-64/lib
endif

ifeq ($(ARCH),ARM)
LIBS:=-lpthread
LIBS+=-dl
LIBS+=./libconfig-x86-64/lib/libconfig++.a
#LIBS+=-lconfig++
else
LIBS:=-lpthread
LIBS+=-dl
LIBS+=./libconfig-x86-64/lib/libconfig++.a
#LIBS+=-lconfig++
endif

ifeq ($(ARCH),ARM)
TARGET:=lx.bin
else
TARGET:=lx.bin
endif

$(TARGET) : $(SRC)
	$(CROSS)g++ $(CFLAG) -o $(TARGET) $^ $(LPATH) $(IPATH) $(LIBS) $(LDFLAG)

clean:
	rm -f  *.bin  *.dis  *.elf  *.o
