all: splice example1

CFLAGS = -Wall -Wextra -O2 -g
CXXFLAGS = $(CFLAGS)
CXX = c++

libjson.a: ../src/json.c
	$(CC) $(CFLAGS) -c -o $@ ../src/json.c $(CPPFLAGS)

splice: splice.c libjson.a
	$(CC) $(CFLAGS) -o $@ splice.c libjson.a $(CPPFLAGS) -I../src -lm

splice.cc: splice.c
	ln -f $(@:.cc=.c) $@

splice++: splice.cc libjson.a
	$(CXX) $(CXXFLAGS) -o $@ splice.cc libjson.a $(CPPFLAGS) -I../src -lm

example1: example1.c libjson.a
	$(CC) $(CFLAGS) -o $@ example1.c libjson.a $(CPPFLAGS) -I../src -lm

.PHONY: clean clean~

clean:
	rm -rf example1 splice splice++ splice.cc libjson.a *.dSYM

clean~: clean
	rm -f *~
