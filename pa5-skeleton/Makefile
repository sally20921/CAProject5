#----------------------------------------------------------------------
# 
#  4190.308 Computer Architecture (Fall 2018)
#
#  Project #5: Optimizing Performance on a Pipelined Y86-64 Processor
#
#  December 4, 2018
#
#  Jin-Soo Kim (jinsoo.kim@snu.ac.kr)
#  Systems Software & Architecture Laboratory
#  Dept. of Computer Science and Engineering
#  Seoul National University
#  http://csl.snu.ac.kr
#
#----------------------------------------------------------------------

CAT 	= /bin/cat

YAS 	= 						# SET THIS VALUE (e.g., ../pa4-skeleton/sim/misc/yas)
SSIM 	= 						# SET THIS VALUE (e.g., ../pa4-skeleton/sim/seq/ssim)
SSIMFLAGS = -s

ifndef YAS
$(error YAS is not set)
endif

ifndef SSIM
$(error SSIM is not set)
endif

TARGET	= bmptest.yo
ASRCS	= bmptest.ys
YSRCS	= bmpmain.ys bmpmosaic.ys
MEMOUT  = memory.out
MEMANS  = result.out

all: $(TARGET)

$(TARGET): $(ASRCS)
	$(YAS) $(ASRCS) $@

$(ASRCS): $(YSRCS)
	$(CAT) $(YSRCS) > $(ASRCS)

clean:
	$(RM) -f $(TARGET) $(ASRCS) $(MEMOUT) *~

run: $(TARGET)
	$(SSIM) $(TARGET)

testrun: $(TARGET)
	$(SSIM) $(SSIMFLAGS) $(TARGET)

test: 
	@rm -f $(MEMOUT)
	@make testrun
	@diff $(MEMOUT) $(MEMANS) && echo "Test: SUCCESS"
