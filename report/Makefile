
#outputs $(PROJFILE).{dvi,pdf,ps,...}
PROJNAME = submodularity

#do not include .tex
SOURCEFILE = main

#other files $(SOURCEFILE).tex includes, eg .bib files, etc.
#DO include .tex, .bib, ...
INCLUDES = 
#ENV      = env TEXINPUTS=".:styles/:" BSTINPUTS=".:styles/:"
ENV      =
BIBTEX   = $(ENV) bibtex
LATEX    = $(ENV) latex
DVIPS    = dvips
PDFLATEX = $(ENV) pdflatex
EPSTOPDF = epstopdf

default: pdf

.PHONY: default all dvi ps pdf clean clobber

all: dvi ps pdf

view: pdf
	acroread $(PROJNAME).pdf

dvi: $(PROJNAME).dvi
ps:  $(PROJNAME).ps
pdf: $(PROJNAME).pdf

$(PROJNAME).dvi: $(SOURCEFILE).tex $(INCLUDES)
	$(LATEX) $(SOURCEFILE).tex
	$(BIBTEX) $(SOURCEFILE).aux
	$(LATEX) $(SOURCEFILE).tex
	$(LATEX) $(SOURCEFILE).tex
	$(LATEX) $(SOURCEFILE).tex
	mv -f $(SOURCEFILE).dvi $(PROJNAME).dvi

$(PROJNAME).ps: $(PROJNAME).dvi
	$(DVIPS) $(PROJNAME).dvi -o $(PROJNAME).ps

$(PROJNAME).pdf: $(SOURCEFILE).tex $(INCLUDES)
	$(PDFLATEX) $(SOURCEFILE).tex
	$(BIBTEX) $(SOURCEFILE).aux
	$(PDFLATEX) $(SOURCEFILE).tex
	$(PDFLATEX) $(SOURCEFILE).tex
	$(PDFLATEX) $(SOURCEFILE).tex
	mv -f $(SOURCEFILE).pdf $(PROJNAME).pdf

clean:
	rm -f *.aux *.log *.nav *.out *.snm *.toc *.bbl *.blg *_out.aux *_out.log *_out.nav *_out.snm *_out.toc *_out.tex $(SOURCEFILE).dvi $(SOURCEFILE).pdf $(SOURCEFILE).aux $(SOURCEFILE).log $(SOURCEFILE).nav $(SOURCEFILE).out $(SOURCEFILE).snm $(SOURCEFILE).toc $(SOURCEFILE).bbl $(SOURCEFILE).blg *~

clobber: clean
	rm -f $(PROJNAME).dvi $(PROJNAME).ps $(PROJNAME).pdf

