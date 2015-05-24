# PenMesh: Monte Carlo Simulation of Radiation Transport in Triangle Meshes #


PenMesh is a software package that combines a state-of-the-art Monte Carlo simulation algorithm and a modern computed-aided design (CAD) geometry model with the purpose of simulating radiation transport across complex, free-form objects. PenMesh uses the particle transport physics from the PENELOPE 2006 package and a geometry model in which objects are defined by closed triangle meshes. The main program, tally and source routines are based on the penEasy 2006 package, extended with the tools from the penEasy\_Imaging package to be able to generate a radiographic image as the output of the simulation. Currently, the main application of penMesh is the simulation of clinical x-ray imaging systems using detailed anatomical phantoms. However, the code is general enough to simulate any other situation involving photon, electron or positron transport, as long as the simulation stays within the applicability range of PENELOPE.

PenMesh was developed at the _U. S. Food and Drug Administration (FDA), Center for Devices and Radiological Health, Office of Science and Engineering Laboratories_, [Division of Imaging and Applied Mathematics](http://www.fda.gov/MedicalDevices/ScienceandResearch/ucm2007489.htm). Partial funding for the development of this software has been provided by the FDA _Office of Women's Health_ and by the FDA _Office of the Chief Scientist_ through the Computational Endpoints for Cardiovascular Device Evaluations project.

The source code and documentation of penMesh are openly distributed at the website: http://code.google.com/p/penmesh/ . The following disclaimer notice applies to the code and documentation developed exclusively at the FDA (this disclaimer is provided at the beginning of each file developed at the FDA):


## Code disclaimer ##

This software and documentation (the "Software") were developed at the Food and Drug Administration (FDA) by employees of the Federal Government in the course of their official duties. Pursuant to [Title 17, Section 105 of the United States Code](http://www.copyright.gov/title17/92chap1.html#105), this work is not subject to copyright protection and is in the public domain. Permission is hereby granted, free of charge, to any person obtaining a copy of the Software, to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, or sell copies of the Software or derivatives, and to permit persons to whom the Software is furnished to do so. FDA assumes no responsibility whatsoever for use by other parties of the Software, its source code, documentation or compiled executables, and makes no guarantees, expressed or implied, about its quality, reliability, or any other characteristic. Further, use of this code in no way implies endorsement by the FDA or confers any advantage in regulatory decisions. Although this software can be redistributed and/or modified freely, we ask that any derivative works bear some notice that they are derived from it, and any modified versions bear some notice that they have been modified.



---



## Code documentation and main reference ##

A manuscript describing in detail the algorithms implemented in penMesh has been published in the IEEE Transaction on Medical Imaging journal. The users of penMesh are encouraged to read this paper for further reference and also to cite it in their scientific publications:

  * A. Badal, I. Kyprianou, D. P. Banh, A. Badano, and J. Sempau, "penMesh—Monte Carlo radiation transport simulation in a triangle mesh geometry", IEEE Trans Med Imaging 28 (12), pp. 1894-901 (2009).

ABSTRACT: PenMesh is a general-purpose Monte Carlo simulation code that combines the accuracy of the radiation transport physics subroutines from PENELOPE and the flexibility of a geometry based on triangle meshes. While the geometric models implemented in most general-purpose codes—such as PENELOPE’s quadric geometry—impose some limitations in the shape of the objects that can be simulated, triangle meshes can be used to describe any free-form (arbitrary) object. Triangle meshes are extensively used in computer-aided design and computer graphics. We took advantage of the sophisticated tools already developed in these fields, such as an octree structure and an efficient ray-triangle intersection algorithm, to significantly accelerate the triangle mesh ray-tracing. A detailed description of the new simulation code and its ray-tracing algorithm is provided in this paper. Furthermore, we show how it can be readily used in medical imaging applications thanks to the detailed anatomical phantoms already available. In particular, we present a whole body radiography simulation using a triangulated version of the anthropomorphic NCAT phantom. An example simulation of scatter fraction measurements using a standardized abdomen and lumbar spine phantom, and a benchmark of the triangle mesh and quadric geometries in the ray-tracing of a mathematical breast model, are also presented to show some of the capabilities of penMesh.

Other publications that describe the implemented algorithms or present example applications of penMesh are listed below:

  * A. Badal, "Development of advanced geometric models and acceleration techniques for Monte Carlo simulation in Medical Physics", PhD dissertation, Universitat Politecnica de Catalunya (2008). ISBN: 978-84-691-6235-4. Thesis available at: http://www.tesisenxarxa.net/TDX-0523108-095624/

  * A. Badal, I. Kyprianou, A. Badano and J. Sempau, "Monte Carlo simulation of a realistic anatomical phantom described by triangle meshes: application to prostate brachytherapy imaging", Radiotherapy and Oncology 86, pp. 99-103 (2007).

  * A. Badal, I. S. Kyprianou, A. Badano, J. Sempau and K. J. Myers, "Monte Carlo package for simulating radiographic images of realistic anthropomorphic phantoms described by triangle meshes", SPIE Medical Imaging 2007: Physics of Medical Imaging, Proc. SPIE 6510 (2007).


## External software used by penMesh: PENELOPE and penEasy ##

**PENELOPE** (version 2006) is a general purpose code that performs Monte Carlo simulation of coupled electron-photon transport in arbitrary materials and in the energy range from 50 eV to 1 GeV. The standard geometry model used by PENELOPE (PENGEOM) is based on defining objects as the volume limited by a set of quadric surfaces. Despite this model can be used to describe complex geometries, it is not adequate to represent biological structures with arbitrary shapes. The PENELOPE subroutines are copyrighted by the Universitat de Barcelona and can be obtained for free at http://www.nea.fr/abs/html/nea-1525.html or at http://www-rsicc.ornl.gov/ . A comprehensive description of the physical and geometrical models implemented in PENELOPE 2006 can be found at:

  * F. Salvat, J. M. Fernandez-Varea and J. Sempau, "PENELOPE, A Code System for Monte Carlo Simulation of Electron and Photon Transport", Workshop Proceeding Issy-les-Moulineaux OECD/NEA 7-10 July 2003. ISBN: 92-64-02145-0. Document available at http://www.nea.fr/html/dbprog/penelope-2003.pdf .

```
    CCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCC
    C  PENELOPE/PENGEOM (version 2006)                                     C
    C  Copyright (c) 2001-2006                                             C
    C  Universitat de Barcelona                                            C
    C                                                                      C
    C  Permission to use, copy, modify, distribute and sell this software  C
    C  and its documentation for any purpose is hereby granted without     C
    C  fee, provided that the above copyright notice appears in all        C
    C  copies and that both that copyright notice and this permission      C
    C  notice appear in all supporting documentation. The Universitat de   C
    C  Barcelona makes no representations about the suitability of this    C
    C  software for any purpose. It is provided "as is" without express    C
    C  or implied warranty.                                                C
    CCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCC
```



**PenEasy** is a general-purpose simulation package for PENELOPE developed by Josep Sempau. The package contains a modular main program and several tally options and source models that facilitate the simulation of medical physics applications. The modular structure of the code makes it easy to develop additional tools that extend the applicability of PENELOPE to new fields of study. The main program of penMesh is essentially a translation of penEasy's main program from Fortran 95 to C++. The main program calls most of the original Fortran functions from penEasy, and also some new C++ functions that handle the triangle mesh geometry tracking. A header file with pre-processor directives is used to harmonize the naming conventions between the two programming languages, and a make script is provided to simplify the multi-language compilation. The penEasy package is copyrighted by the Universitat Politecnica de Catalunya and distributed at http://www.upc.es/inte/downloads/penEasy.htm .

```
    cccccccccccccccccccccccccccccccccccccccccccccccccccccccccccccccccccccccccccccccc
    c  penEasy                                                                     c
    c  Copyright (c) 2004-2008                                                     c
    c  Universitat Politecnica de Catalunya                                        c
    c                                                                              c
    c  Permission to use, copy, modify and re-distribute copies of this software   c
    c  or parts of it and its documentation for any purpose is hereby granted      c
    c  without fee, provided that this copyright notice appears in all copies.     c
    c  The Universitat Politecnica de Catalunya makes no representations about     c
    c  the suitability of this software for any purpose. It is provided "as is"    c
    c  without express or implied warranty.                                        c
    cccccccccccccccccccccccccccccccccccccccccccccccccccccccccccccccccccccccccccccccc
```


**PenEasy\_Imaging** is an extension of penEasy that facilitates the simulation of medical imaging systems. The two major extensions provided by PenEasy\_Imaging are a tally module to generate radiographic images as the output of the x-ray transport simulation and a rectangular beam, or fan beam, source model that emits a collimated beam of radiation instead of a cone beam. This code is openly distributed at the website: http://code.google.com/p/peneasy-imaging/ .

This documentation has been automatically generated parsing the comments in the penMesh source code using the Doxygen software (http://www.doxygen.org).


## Code compilation and usage ##

PenMesh can be compiled in the Linux operating system using the make utility and the provided Makefile scripts. The user may have to edit the Makefile to modify the name of the C and Fortran compilers and give the correct paths to their libraries. The penMesh package does NOT include the source code files from PENELOPE. To compile the code, the users have to obtain the PENELOPE 2006 package and copy the required source files to the folder specified in the Makefile script. For convenience, compiled versions of penMesh are provided.

The default PENELOPE library defines a maximum of 10 materials to be used in the simulation. PenMesh uses a limit of 20 materials. To change the maximum number of materials the files penelope.f and penvared.f have to be edited to change all the lines containing "MAXMAT=10" to "MAXMAT=20". Then this files have to be saved as penelope\_MAXMAT20.f and penvared\_MAXMAT20.f, the name expected by the Makefile script. A list of all the lines that have to be changed can be obtained in a Linux shell with the command: grep -ni "MAXMAT=10" **.f.**

To begin a penMesh simulation, the input file specifying the geometry, material data and code options has to be re-directed to the executable's standard input at execution time. The input file describing the triangle mesh geometry can be given as an input parameter; in case no name is given, the default file triangle\_geometry.in is used.

```
   $./penMesh.x [triangle_geometry.in] < input.in > output.out &
```

Read the original documentation from the penEasy and penEasy\_Imaging, distributed with the penMesh package, for more information on the use of the available source models and tallies. GNUplot scripts are provided to graphically visualize the output of the different tallies at the end of the simulation.

Questions, bug reports, feature suggestions, etc, can be posted in the [Issues section](http://code.google.com/p/penmesh/issues/list) in this website. For further information, the users can also directly contact the code developer at the address: Andreu.Badal-Soler (at) fda.hhs.gov.


---



**Authors:**
> Andreu Badal and Iacovos Kyprianou

**Date:**
> September 17, 2010

**Version:**
> 2010-09-17