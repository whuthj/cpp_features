CC=g++
CFLAGS=-std=c++11 -g -Wall
TARGET=hook.t s_hook.t
#OBJS=$(patsubst %.cpp, %.o, $(wildcard *.cpp))
OBJS=$(patsubst %, %.o, $(TARGET))

all : $(TARGET)

s_%.t: %.o
	@$(CC) $(CFLAGS) $^ -o $@ -L.. -lcoroutine -static -static-libgcc -static-libstdc++
	@echo "LD $(TARGET)"

%.t: %.o
	@$(CC) $(CFLAGS) $^ -o $@ -L.. -lcoroutine -ldl
	@echo "LD $(TARGET)"

.cpp.o:
	@$(CC) $(CFLAGS) -c $^ -I.. -o $@
	@echo "MK $@"

.PHONY: clean

clean:
	rm *.o $(TARGET) -f
