##
##  Libmonitor src/Makefile.am.
##
##  Copyright (c) 2007-2013, Rice University.
##  All rights reserved.
##
##  Redistribution and use in source and binary forms, with or without
##  modification, are permitted provided that the following conditions are
##  met:
##
##  * Redistributions of source code must retain the above copyright
##    notice, this list of conditions and the following disclaimer.
##
##  * Redistributions in binary form must reproduce the above copyright
##    notice, this list of conditions and the following disclaimer in the
##    documentation and/or other materials provided with the distribution.
##
##  * Neither the name of Rice University (RICE) nor the names of its
##    contributors may be used to endorse or promote products derived from
##    this software without specific prior written permission.
##
##  This software is provided by RICE and contributors "as is" and any
##  express or implied warranties, including, but not limited to, the
##  implied warranties of merchantability and fitness for a particular
##  purpose are disclaimed. In no event shall RICE or contributors be
##  liable for any direct, indirect, incidental, special, exemplary, or
##  consequential damages (including, but not limited to, procurement of
##  substitute goods or services; loss of use, data, or profits; or
##  business interruption) however caused and on any theory of liability,
##  whether in contract, strict liability, or tort (including negligence
##  or otherwise) arising in any way out of the use of this software, even
##  if advised of the possibility of such damage.
##
##  $Id$
##

MONITOR_MAIN_FILES = callback.c main.c mpi.c utils.c
MONITOR_THREAD_FILES = pthread.c
MONITOR_SCRIPT_FILES = monitor-link monitor-run
MONITOR_MPI_FILES =  \
	mpi_init_c.c  mpi_init_thread_c.c  mpi_final_c.c  mpi_comm_c.c   \
	mpi_init_f0.c mpi_init_thread_f0.c mpi_final_f0.c mpi_comm_f0.c  \
	mpi_init_f1.c mpi_init_thread_f1.c mpi_final_f1.c mpi_comm_f1.c  \
	mpi_init_f2.c mpi_init_thread_f2.c mpi_final_f2.c mpi_comm_f2.c

include_HEADERS = monitor.h
bin_SCRIPTS =
CLEANFILES = $(MONITOR_SCRIPT_FILES)

if MONITOR_TEST_LINK_PRELOAD
    lib_LTLIBRARIES = libmonitor.la
    libmonitor_la_SOURCES = $(MONITOR_MAIN_FILES)
    libmonitor_la_CPPFLAGS = -DMONITOR_DYNAMIC
    bin_SCRIPTS += monitor-run
if MONITOR_TEST_USE_DLOPEN
    libmonitor_la_SOURCES += dlopen.c
endif
if MONITOR_TEST_USE_FORK
    libmonitor_la_SOURCES += fork.c
endif
if MONITOR_TEST_USE_PTHREADS
    libmonitor_la_SOURCES += $(MONITOR_THREAD_FILES)
endif
if MONITOR_TEST_USE_SIGNALS
    libmonitor_la_SOURCES += signal.c
endif
if MONITOR_TEST_USE_MPI
    libmonitor_la_SOURCES += $(MONITOR_MPI_FILES) pmpi.c
endif
if MONITOR_TEST_USE_GNU_ATOMIC_OPS
    libmonitor_la_CPPFLAGS += -DUSE_GNU_ATOMIC_OPS
endif
endif

if MONITOR_TEST_LINK_STATIC
    lib_LIBRARIES = libmonitor_wrap.a
    libmonitor_wrap_a_SOURCES = $(MONITOR_MAIN_FILES)
    libmonitor_wrap_a_CPPFLAGS = -DMONITOR_STATIC
    bin_SCRIPTS += monitor-link
if MONITOR_TEST_USE_DLOPEN
    libmonitor_wrap_a_SOURCES += dlopen.c
endif
if MONITOR_TEST_USE_FORK
    libmonitor_wrap_a_SOURCES += fork.c
endif
if MONITOR_TEST_USE_PTHREADS
    libmonitor_wrap_a_SOURCES += $(MONITOR_THREAD_FILES)
endif
if MONITOR_TEST_USE_SIGNALS
    libmonitor_wrap_a_SOURCES += signal.c
endif
if MONITOR_TEST_USE_MPI
    libmonitor_wrap_a_SOURCES += $(MONITOR_MPI_FILES)
endif
if MONITOR_TEST_USE_GNU_ATOMIC_OPS
    libmonitor_wrap_a_CPPFLAGS += -DUSE_GNU_ATOMIC_OPS
endif
endif
