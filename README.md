<a name="top"></a>

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Open Source? Yes!](https://badgen.net/badge/Open%20Source%20%3F/Yes%21/blue?icon=github)](https://github.com/Naereen/badges/)
![Mastodon Follow](https://img.shields.io/mastodon/follow/114193593282968080?domain=wisskomm.social)
<!--[![Maintenance](https://img.shields.io/badge/Maintained%3F-yes-green.svg)](https://github.com/remsens-lim/pyMakeRetrieval/graphs/commit-activity) -->

# BOWTIE_LIM-instrument-processing

<!-- TABLE OF CONTENTS -->
<details>
  <summary>Table of Contents</summary>
  <ol>
    <li><a href="#Introduction">Introduction</a></li>
    <li><a href="#HATPRO">HATPRO</a></li>
    <li><a href="#Cloud_radar">Cloud radar</a></li>
    <li><a href="#rain_flag">MRR-based rain flag</a></li>
    <li><a href="#Ceilometer">Ceilometer</a></li>
    <li><a href="#license">License</a></li>
    <li><a href="#contact">Contact</a></li>
    <li><a href="#acknowledgments">Acknowledgments</a></li>
  </ol>
</details>


<!-- Introduction -->
## Introduction

In this repository the LIM team stores the BOWTIE post processing scripts of the microwave radiometer HATPRO, motion stabilized 94 GHz cloud radar, ceilometer, a rain flag based on a micro rain radar and cloudnet products.

<!-- HATPRO -->
## HATPRO

HATPRO data was processed using mwrpy on the ACTRIS/Cloudnet server (https://github.com/actris-cloudnet/mwrpy). Therefore the HATPRO raw binaries were uploaded. After the processing we downloaded the single- and multi-pointing *.nc files. We added the global attributes according to the IPFS standards and saved the output as *.zarr files using the ~/instruments/HATPRO/HATPRO_postprocessing.ipynb.

<!-- Cloud_radar -->
## Cloud radar

The installation of the cloud radar on the ship, as well as operational the settings induced errors into the data which we corrected for. Besides an approved despeckling routine (by Willi Schimmel), which is based on the identification of isolated pixels, other major issues are tackled. Doppler spectrum folding caused the chosen unambiguous range of velocities is accounted for by a newly adapted dealiasing routine (A. Kötsche and A.Trosits) based on previous work by Willi Schimmel. After this, the heave motion (up and down) of the ship needs to be subtracted from the Doppler spectra, which is done as for the EUREC4A data set (https://github.com/remsens-lim/eurec4a). Additionally, ghost echos are flagged and if isolated also removed. This data set was uploaded to the Cloudnet data portal to derive additional cloud microphysical  variables such as eg. ice and droplet effective radii and to classify the observed targets. Following to this the vertical reolution was unified and a rain attenuation flag based on the doppler velocity at signal top height and rain rates at the ground was added to the dataset. 

<!-- #ain_flag -->
## MRR-based rain flag
Micro rain radar raw data was stored in *.nc. We used the thirdlowest rangebin (156m) and a Ze threshold of 3 dBZ to identify surface rain. Afterwards, we added the global attributes according to the IPFS standards and saved the output as *.zarr files using the ~/instruments/MRR/MRR_processing.ipynb.

<!-- Ceilometer -->
## Ceilometer
Ceilometer raw data was stored in *.nc files. We added the global attributes according to the IPFS standards and saved the output as *.zarr files using ~/instruments/Ceilometer/Ceilometer_postprocessing.ipynb.

<!-- Cloudnet -->
## Cloudnet products
Cloudnet products were downloaded from https://cloudnet.fmi.fi. We added the global attributes according to the IPFS standards and saved the output as *.zarr files using ~/instruments/cloudnet_product/Cloudnet_products_postprocessing.ipynb.


<!-- LICENSE -->
## License

Distributed under the MIT License. See `LICENSE` for more information.

<p text-align="right">(<a href="#top">back to top</a>)</p>

<!-- CONTACT -->
## Contact

[Andreas Foth](https://www.uni-leipzig.de/personenprofil/mitarbeiter/dr-andreas-foth)


<p text-align="right">(<a href="#top">back to top</a>)</p>

<!-- ACKNOWLEDGMENTS -->
## Acknowledgments

Special thanks for templates and help during implementation.

* [cloudnetpy GitHub](https://github.com/actris-cloudnet/cloudnetpy.git)
* [mwrpy GitHub](https://github.com/actris-cloudnet/mwrpy.git)

<p text-align="right">(<a href="#top">back to top</a>)</p>
