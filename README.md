# Modified Version of "Stardust": Composite Template Fitting Software
For the original version, please see [here](https://github.com/VasilyKokorev/stardust) and [Kokorev et al. 2021](https://ui.adsabs.harvard.edu/abs/2021ApJ...921...40K/abstract).

------

## This Modified stardust code allows AGN fluxes as additional constraints.
The original code fit the model SED F<sub>model</sub>=F<sub>1</sub>+F<sub>2</sub>+F<sub>3</sub> to the data SED F<sub>tot</sub> by minimizing ||F<sub>tot</sub> - F<sub>model</sub>||<sub>2</sub>, where 

  F<sub>1</sub>=UV/Optical stellar light templates or [Shen et al. 2016](https://ui.adsabs.harvard.edu/abs/2016ApJ...817...55S) quasar temperates  
  F<sub>2</sub>=AGN heated dust in the MIR  
  F<sub>3</sub>=IR dust reprocessed stellar light in the NIR-FIR  

When total flux F<sub>tot</sub> is decomposed into the point source (AGN) F<sub>AGN</sub> and rest F<sub>host galaxy</sub> by image decomposition, this modified code can include this additional constraint by providing F<sub>AGN</sub> as AGN_EXTRA_BANDS_FILE and setting AGN_EXTRA_BANDS=1 in the config file (similar to setting EXTRA_BANDS_FILE and EXTRA_BANDS=1). 

  When the stellar light templates are chosen, the code minimizes ||(F<sub>tot</sub>-F<sub>model</sub>)+(F<sub>AGN</sub> - F<sub>2</sub>)||<sub>2</sub>.

  When the quasar templates are chosen, the code minimizes ||(F<sub>tot</sub>-F<sub>model</sub>)+(F<sub>AGN</sub> - F<sub>1</sub> - F<sub>2</sub>)||<sub>2</sub>.

See descriptions: [Tsukui, Wisnioski, Krumholz and Battisti, 2023](https://ui.adsabs.harvard.edu/abs/2023arXiv230207272T/abstract)

##Usage

For a quick example of how to use and reproduce the result [Tsukui et al. 2023](https://ui.adsabs.harvard.edu/abs/2023arXiv230207272T/abstract),  
See [here](https://github.com/takafumi291/stardust/blob/master/modified_example/Modified_Stardust_Example.ipynb) 

## Contacts
Takafumi Tsukui: tsukuitk23@gmail.com

## README of the original stardust below (The same installation instructions and requirements apply)

------

**Stardust** is a Python package designed to extract galaxy properties by fitting their multiwavelength data to a set of linearly combined templates.

This algorithm brings together three different families of templates:

1. UV+Optical emission from dust unobscured stellar light
2. AGN heated dust in the MIR
3. IR dust reprocessed stellar light in the NIR-FIR

One of the features of **Stardust** is that the template fitting does not rely on energy balance. As a result, the total luminosity of dust obscured and dust unobscured stellar light do not rely on each other, and it is possible to fit objects (e.g. SMGs) where the energy balance approach might not be necessarily applicable. A detailed description of **Stardust** and its first application is presented in [Kokorev et al. 2021](https://ui.adsabs.harvard.edu/abs/2021ApJ...921...40K/abstract).

## Requirements

```
python
python>=3.9.0
numpy
scipy
matplotlib
astropy
multiprocess
tqdm
```

## Installation

For MacOS users, it is recommended to create a separate **Python 3.6.10** environment with miniconda. See instructions [here](https://docs.conda.io/projects/conda/en/latest/user-guide/tasks/manage-environments.html).

You can then pull Stardust and install it with pip.

```
$ git clone https://github.com/VasilyKokorev/stardust.git
$ cd stardust
$ pip install .
```

## Usage

The primary use of this code is to extract the parameters from the infrared photometry. The program also has the ability to fit AGN and Stellar emission templates if the user desires to do so. It is recommended to use this code within a Jupyter notebook.

See [here](https://github.com/VasilyKokorev/stardust/blob/master/example/Stardust_Example.ipynb) for a quick example of how to fit a catalogue.

An example dataset, a subset from the [COSMOS Super-Deblended Catalogue 2 (Jin+18)](https://ui.adsabs.harvard.edu/abs/2018ApJ...864...56J/abstract) along with the example configuration files are provided in the [example folder](https://github.com/VasilyKokorev/ctf/tree/master/example).

See the [quickstart guide](https://github.com/VasilyKokorev/ctf/blob/master/docs/README.md) and [docs folder](https://github.com/VasilyKokorev/ctf/tree/master/docs) for more detailed instructions.

## Acknowledgements

Filter curves are adopted from [eazy-py](https://github.com/gbrammer/eazy-py) by Gabe Brammer.

## Troubleshooting

**1. The module does not install:** If you are on Linux, try using Python 3.9.1 instead.

## Contacts

Vasily Kokorev: vasily.kokorev.astro@gmail.com / kokorev@astro.rug.nl
