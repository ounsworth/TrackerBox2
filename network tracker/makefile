# 1. which compiler to use
Cxx=g++

# 2. compiler flags
CXXFLAGS = -Wall `pkg-config --cflags opencv yaml-cpp`
VALGRIND_FLAGS = -g -O0

# 3. libraries to link against
OpenCVLibs = `pkg-config --libs opencv`
YAMLLibs = `pkg-config --libs yaml-cpp`
OTHERLibs = -lpthread -lzmq

# 4. name of the output executable
OUTPUT_EXE = networkTracker

# 5. rules

all: $(OUTPUT_EXE)

$(OUTPUT_EXE): networkTracker.cpp networkTracker.h networkTrackerYAML_utils.o
	$(Cxx) $(CXXFLAGS) -O2 $(filter-out %.h, $^) -o $@ $(OpenCVLibs) $(YAMLLibs) $(OTHERLibs)

networkTrackerYAML_utils.o: networkTrackerYAML_utils.h networkTrackerYAML_utils.cpp
	$(Cxx) $(CXXFLAGS) -O2 -c $(filter-out %.h, $^) $(YAMLLibs)

clean:
	rm -f *~ *.o $(OUTPUT_EXE)
