MAPPAGES := $(shell ls maps/*.md)
MAPHTMLS := $(addprefix out/,$(MAPPAGES:.md=.html))

TLPAGES := $(shell ls timelines/*.md)
TLHTMLS := $(addprefix out/,$(TLPAGES:.md=.html))

#---
.PHONY: main
main: $(MAPHTMLS) $(TLHTMLS)

.PHONY: clean
clean:
	rm -fr out tmp

out/maps/%.html: maps/%.md Makefile
	mkdir -p $(@D)
	markmap --no-open -o $@ $<

out/timelines/%.html: timelines/%.md Makefile
	mkdir -p $(@D)
	pandoc -o $@ --from markdown --standalone -M title="Timeline" \
	-V mainfont='"Segoe UI","Noto Sans",Helvetica,Arial,sans-serif' \
	-V maxwidth=64em $<
