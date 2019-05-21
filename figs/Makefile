.PHONY : figs 

figs : linked_selection_figs aurantiacus_figs fst_tree.png background_haps.png sweep_haps.png from_the_literature/langley-et-al-2012-chr3-pi-and-rho.png 
	
linked_selection_figs : linked-selection-guide/linked-selection-site-neutral.png linked-selection-guide/linked-selection-site-neutral_early.png linked-selection-guide/linked-selection-site-hard.png linked-selection-guide/linked-selection-site-soft.png linked-selection-guide/linked-selection-site-recent_balancing.png linked-selection-guide/linked-selection-site-old_balancing.png linked-selection-guide/linked-selection-site-introgression.png linked-selection-guide/linked-selection-site-local_adaptation.png linked-selection-guide/linked-selection-region-background.png linked-selection-guide/linked-selection-region-recurrent_sweeps.png linked-selection-guide/linked-selection-region-recurrent_introgression.png

aurantiacus_figs : aurantiacus/labeled_phylogeny_puniceus.png aurantiacus/labeled_phylogeny_long-caly.png aurantiacus/labeled_phylogeny_caly.png aurantiacus/labeled_phylogeny_aura.png aurantiacus/labeled_phylogeny_arid-parv.png aurantiacus/labeled_phylogeny_parv.png aurantiacus/labeled_phylogeny_gran.png aurantiacus/labeled_phylogeny_all.png

aurantiacus/labeled_phylogeny_%.pdf : aurantiacus/labeled_phylogeny.ink.svg
	./export-layers-svg.sh $< phylogeny $* > $@

linked-selection-guide/linked-selection-site-%.pdf : linked-selection-guide.ink.svg
	./export-layers-svg.sh $< axes site $* >$@

linked-selection-guide/linked-selection-region-%.pdf : linked-selection-guide.ink.svg
	./export-layers-svg.sh $< axes region $* >$@

## image conversion

%.pdf : %.svg
	inkscape $< --export-pdf=$@

# %.svg : %.pdf
# 	inkscape $< --export-plain-svg=$@

%.png : %.pdf
	convert -density 300 $< -flatten $@

%.gif : %.pdf
	convert -density 300 $< -flatten $@

%.png : %.svg
	convert -density 300 $< -flatten $@

%.gif : %.svg
	convert -density 300 $< -flatten $@

%.pdf : %.ink.svg
	inkscape $< --export-pdf=$@

# animated gif
%.anim.gif : $(wildcard %/*.gif)
	convert -loop 0 -delay 10 -coalesce -fuzz 2% -layers optimize $$(ls $*/*.gif) $@
