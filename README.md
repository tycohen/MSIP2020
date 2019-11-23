MSIP 2020 Proposal
Population Synthesis Dataset
=======

.par files and RMS noise estimates for a simulated galactic population of MSPs observed with a variety of instrument configurations. A description of the population generation is at http://www.aoc.nrao.edu/~tcohen/research/popsynth.shtml.

.par files and ASCII files are located in the *data/* directory. The population is split into "include" and "exclude" where excluded MSPs have RMS values that are similar to real NANOGrav RMSs at their respective telescopes and included MSPs should be added to the PTA in the future.

----------
## .par files
.par files are Tempo(2)-compatible and contain the following parameters:

* **PSRJ :** j-name from RA & Dec, includes arcseconds in case coincident pulsars
* **RAJ** 
* **DECJ**
* **PMRA :** set to zero, only total PM is computed by simulations
* **PMDEC :** set to zero, only total PM is computed by simulations
* **P0**
* **PEPOCH :** set to MJD of date of file creation
* **DM**
* **P1**
* **PX**

All parameters are set to fit.

-----------
## ASCII files
The ASCII files contain simulated attributes (some of this is redundant with the .par files) of the MSPs and RMS components computed for a specific intstrument configuration. Details about the instrument configuration and underlying population distribution are located in the file header. Pulsars are sorted by the total TOA uncertainty. If all you want is the noise parameters, just grab columns 18-24. The columns of the ASCII files are:

* **Name :** jname of pulsar
* **Period_ms :** pulse period in ms
* **Pdot :** period derivative (s s^-1)
* **DM :** NE2001 DM in pc cm^-3
* **t_scatter :** scattering timescale in ms
* **Width_ms :** intrinsic pulse width in ms
* **GL :** galactic latitude in deg
* **GB :** galactic longitude in deg
* **RA :** right ascension in fractional deg
* **DEC :** declination in fractional deg
* **S1400 :** flux at 1.4 GHz in mJy
* **L1400 :** luminosity at 1.4 GHz in mJy kpc^2
* **SPINDEX :** spectral index
* **DTRUE :** true distance in kpc from radius and scale height
* **X, Y, Z :** galactic cartesian positions

Noise parameters are set to -2 if the pulsar is outside of the telescope
declination limits and -1 if the pulsar is too dim or smeared out to be
timed reliably:

* **sigma_toa :** total TOA uncertainty quad sum of sigma_w, sigma_dm, sigma_tel in us (see Lam et al., 2018)
* **sigma_tel :** telescope noise us (RFI, gain cal, polarization)
* **sigma_dm :** DM estimation uncertainty in us
* **sigma_w :** white noise errors in us (quad sum of radiometer, jitter, scintillation error)
* **sigma_j :** jitter noise in us (see t_int in header to scale)
* **rn_amp :** red noise pwr spec amplitude in us yr^1/2 (see Cordes & Shannon, 2010)
* **rn_index :** red noise pwr spectral index (see NG 9-yr timing)

### ASCII Header
Timing Parameters

* **t_int :** integration time per epoch (s)
* **nus :** frequency range of instrument(s) (GHz)
* **ctrfreq :** center of instrument frequency range (GHz)
* **bw :** bandwidth of instrument frequency range (GHz)
* **Trxs :** frequency-dependent receiver temperature (Tsys - Tgal - TCMB, K)
* **Gains :** frequency-dependent gain of instrument (K Jy^-1)
* **Eps :** fractional gain error of instrument
* **interp :** interpolate receiver T and gain between frequencies
* **rx_freq :** frequency bins for Trx and Gain (GHz)
* **ra_lim :** right-ascension limits of telescope (deg)
* **dec_lim :** declination limits of telescope (deg)

Population Model parameters

* **Date_Generated :** date of model creation (for versioning)
* **n_psrs :** number of pulsars in model
* **n_timed :** number of pulsars successfully timed
* **ndet :** number of pulsars detected in surveyList
* **electronModel :** electron distribution model of the galaxy
* **lumDistType :** pdf of luminosity used in model
* **lumsigma :** std of luminosity distribution (mJy kpc^2)
* **radialDistType :** pdf of galactic radial distribution used in model
* **velDistType :** pdf of birth-velocity used in model
* **velmean :** mean of velocity distribution (km s^-1)
* **velsigma :** std of velocity distribution (km s^-1)
* **pDistType :** pdf of period used in model
* **pmean :** mean of period distribution (ms)
* **psigma :** std of period distribution (ms)
* **zscale :** mean of scale height distribution (kpc)
* **rn_lnC2 :** Cordes & Shannon (2010) red noise power law ln(C2) parameter
* **rn_alpha :** Cordes & Shannon (2010) red noise power law alpha parameter
* **rn_beta :** Cordes & Shannon (2010) red noise power law beta parameter
* **rn_gamma :** Cordes & Shannon (2010) red noise power law gamma parameter
* **rn_delta :** Cordes & Shannon (2010) red noise power law delta parameter
* **simean :** mean of spectral index distribution
* **sisigma :** std of spectral index distribution
* **brokenSI:** broken power-law spectral index
* **brokenFrac :** fraction of pulsars with broken power law spectra
* **gpsfrac :** GPS fraction
