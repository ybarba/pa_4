scripts
=======

# Basic info

This folder contains the praat scripts you will use to clean original 
audio files and extract data from a production task. 
They should be run in order (see below). 


# Data structure

The production data has the following structure

```
pa_4
|
├── data
├── recordings
│   ├── README.md
│   ├── bi01
│   │   └── wavs
│   │       ├── 0_normalizeScalePeakIntensity.praat
│   │       ├── bi01_kaka.TextGrid
│   │       ├── bi01_kaka.wav
│   │       ├── bi01_kaka1.TextGrid
│   │       ├── bi01_kaka1.wav
│   │       ├── bi01_kaka2.TextGrid
│   │       ├── bi01_kaka2.wav
|   |       └ ... 
│   ├── bi02
│   │   └── wavs
│   │       ├── 0_normalizeScalePeakIntensity.praat
│   │       ├── bi02_kaka.wav
│   │       ├── bi02_kaka1.wav
│   │       ├── bi02_kaka2.wav
|   |       └ ... 
|   └ ... 
|
├── report
│   └── README.Rmd
|
├── scripts
│   ├── 0_normalizeScalePeakIntensity.praat
│   ├── 1_createTextGrids.praat
│   ├── 2_extractVals.praat
│   └── README.md
|
└── README.md
```

Notice that `bi01` already contains textgrids (you're welcome). 
You need to create them for the remaining participants. 




# Process

The order in which you execute the scripts is important. 
Below you have information about what each script does. 
It is possible that they will not work straightaway (I may have broken them on purpose). 
In other words you need to troubleshoot them and make them work. 
You will need to examine the scripts carefully to understand what they do (tip: read the 
comments). 

1. '0_normalizeScalePeakIntensity.praat'
	- The 'normalizeScalePeakIntensity.praat' script normalizes the peak intensity 
	of all of the files in the 'wav' folders
	- This should be run to every wav folder before moving to (2)
2. '1_createTextGrids.praat'
	- The 'createTextGrids.praat' script reads in every .wav file from the 
	'wav' folder and creates a corresponding textgrid with the same name.
	- The script will create a textgrid with the following tiers: 
	    - release: point tier indicating the stop burst/release
	    - voice: point tier indicating the onset of voicing
	    - vowel: interval tier indicating the beginning/end of the vowel following the stop
	    - note: interval tier for adding any relevant notes (can be left blank, no need to add intervals)
	- The textgrid labels the onset of modal voicing and the stop burst
3. '2_extractVals.praat'
	- The '2_extractVals.praat' file will read in all .wav files and their corresponding textgrids 
	for a given participant in order to extract labeled information from (2).
	- This will create a .csv for the participant and save it in the 'data' directory
	- All the individual .csv files should then be read into R







