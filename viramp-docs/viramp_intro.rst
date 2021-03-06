Usage
=====

This is a general description of the usage and function of each tool found in the `VirAmp pipeline <http://viramp.com/>`_. A more detailed description can be found at the webpage of each tool.

One-click pipeline
------------------

Two general pipelines are provided with a one-click option, one for paired-end data and the other for single-end data.  Users are only required to submit read files and a reference file corresponding to their data.  Alongside the default settings, users may use the "advanced setting" option to custom configure the pipeline with alternative parameters.

.. image:: manual-pic/paired_end_pipeline.png


Quality Control
---------------
First, trim out the low quality bases of the input fastq files. This can be achieved by either removing low quality bases or trimming a certain length from each end.

.. image:: manual-pic/trim_qual.png

Diginorm
--------
Next, reduce coverage and bias using `Digital normalization <http://ged.msu.edu/papers/2012-diginorm/>`_. This step reduces the sample variation as well as sample bias.

.. image:: manual-pic/diginorm.png

`de novo` Contig assembly
------------------------
Now, the pipeline assembles the short reads into longer contigs. By default the **One-click pipeline** uses `velvet <https://www.ebi.ac.uk/~zerbino/velvet/>`_. Two alternatives, `SPAdes <http://bioinf.spbau.ru/spades>`_ and `VICUNA <http://www.broadinstitute.org/scientific-community/science/projects/viral-genomics/vicuna>`_ , are provided and can be selected as either individual tools or through the advanced options in the one-click pipeline.

.. image:: manual-pic/de-novo.png

Reference-based scaffolding
---------------------------
The contigs are then assembled into even longer `super-contigs`. This step is a modification of `AMOScmp <http://sourceforge.net/apps/mediawiki/amos/index.php?title=AMOScmp>`_ 

.. image:: manual-pic/amoscmp.png

Reference-independent scaffolding
---------------------------------
The next step extends the super-contigs and connects them using `SSPACE <http://www.baseclear.com/landingpages/basetools-a-wide-range-of-bioinformatics-solutions/sspacev12/>`_.  The pipeline will produce a draft genome as a multi-fasta file usually containing 5~15 contigs which are listed in the same order as the reference.

.. image:: manual-pic/sspace.png

Gap closing
-----------
This step connects all the contigs in the multi-fasta from the previous step into one linear genome for the convenience of downstream functional analysis.  However, this is **optional** and highly recommended to be done only after assessing the draft genome, as the gaps between the contigs could be from misassembly, sequencing, genome feature, etc. 

.. image:: manual-pic/linear.png 


