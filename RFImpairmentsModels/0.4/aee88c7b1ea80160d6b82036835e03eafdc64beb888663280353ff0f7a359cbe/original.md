Instantiate a non linear PA model, based on a given `model` and is associated parameters.

# Rapp PA model [:Rapp]

First model is Rapp model [1] that is function of a certain `backOff` power and `smoothness` parameter (also called the knee parameter). Rapp non linear power amplifier model is only a AM/AM distortion model and do not affect the phase. It is also possible to specify the theoretical input power value (i.e E[|x[n]|²]). Indded the saturation is defined as a backoff with respect to the input average power. It the power is not specified, the estimated power is first calculated from the time sequence (with 1/N ∑ | x[n]|²). It may lead to bias especially for signal with strong peak to average power ratio. In this case it can be usefull to compute the theoretical power first (and give to this function with `power` keyword) to have a constant saturation value. 
[1] = C. Rapp. Effects of HPA-nonlinearity on a 4-DPSK/OFDM-signal for a digital sound broadcasting signal. In P. S. Weltevreden, editor, ESA Special Publication, volume 332 of ESA Special Publication, Oct. 1991.


# Saleh Model

A second model is the Saleh model that both affect the AM/AM distortion and the AM/PM distortion. The model is parametrized by 4 parameters α*AM, β*AM, α*PM and β*PM.  [2] = A. A. M. Saleh. Frequency-independent and frequency-dependent nonlinear models of TWT amplifiers. 29(11):1715–1720.

# Ghorbani model

A third model is the Ghorbani model that also defines an AM/AM distortion and the AM/PM distortion through a set of 8 parameters, a1,a2,a3,a4 (for the amplitude) and b1,b2,b3,b4 for the phase distortion.

[3] = A. Ghorbani and M. Sheikhan. The effect of solid state power amplifiers (SSPAs) nonlinearities on MPSK and M-QAM signal transmission. In Digital Processing of Signals in Communications, 1991., Sixth International Conference On, pages 193–197

# None model

Pure linear amplification, usefull to be sure no impairments is applied

initNonLinearPA(:Rapp;power=-1,backOff=0,smoothness=0)
- power     : For Rapp model. Theoretical power for constant saturation level. If -1, empirical power is used (default -1)

  * backOff   : For Rapp model. BackOff value, in dB (default 0)
  * smoothness: For Rapp model. Smoothness value (typically between 1 and 10)(default 0)
  * α_AM      : For Saleh model. α parameter for AM distortion (default 0)
  * β_AM      : For Saleh model. β parameter for AM distortion (default 0)
  * α_PM      : For Saleh model. α parameter for PM distortion (default 0)
  * β_PM      : For Saleh model. β parameter for PM distortion (default 0)
  * a1,a2,a3,a4 : For Ghorbani model. Parameters for AM/AM distortion (default all at 0)
  * b1,b2,b3,b4 : For Ghorbbni model. Pbrbmeters for AM/PM distortion (default all at 0)
  * linearGain : For Linear PA model. Applied gain (default 1)
