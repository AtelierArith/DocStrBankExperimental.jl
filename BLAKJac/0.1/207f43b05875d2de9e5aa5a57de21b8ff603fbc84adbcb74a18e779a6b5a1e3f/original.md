BLAKJac*analysis!(sequence::BlochSimulator, trajectorySet::Vector{<:Vector{<:TrajectoryElement}}, options::Dict, saved*H::Dict=Dict())

BLAKJac_Analysis! predicts noise levels, given an RF pattern and a phase encoding pattern.

# Inputs:

A sequence object including an RF pattern, phase-encoding pattern, and a bunch of parameters (see below)

# Output:

  * noisesAll   An array of 3 noise values (rho, T1, T2)
  * ItotAll     Information content (still a very raw metric)
  * b1factorsRMS An array of couplings between (rho, T1, T2) and B1 (and that RMS over the T1T2set); only calculated if handleB1=="sensitivity"
  * CSF_penalty  A penalty for the CSF sensitivity; only calculated if CSF is to be considered

# InOut:

A dictionary of H matrix arrays (labeled by combination of T1T2-probing index and RF pattern name)

# Parameters:

(Note: A meaningful set of options can be pre-defined by "options = Dict(); BLAKJac.BLAKJac_defaults!(trajectorySet, options)")

  * `account_SAR`   If true, the SAR is taken into account in the optimization
  * `considerCyclic`   If set to true, it is assumed that the magnetization state at the beginning of the sequence is the same as at the end thereof.
  * `emphasize_low_freq`   If true, a higher weight is given to the most central region of (ky,kz)
  * `handleB1`   By default ("no"), it is assumed that the only parameters to be reconstructed are T1, T2 and rho; if handleB1=="co-reconstruct",           then BLAKJac assumes that this is a reconstructable parameter as well. If handleB1=="sensitivity", then calculate b1factorRMS
  * `invregval`   An array for (inverses of) the diagonals of a regularization matrix assumed in reconstruction:           A value of 0 assumes no imposed regularisation; a value of 1 assumes that the reconstruction very strongly imposes that the result           should equal the reference values for T1 and T2. The breakeven occurs when invregval is on the order of `abs_sensitivity^2`,           where `abs_sensitivity` is on the order of 0.05, depending on T1, T2 and sequence (very roughly, T2/T1). If the expected SNR is           much larger than 1 (e.g. 10), the invregval should be significantly smaller, e.g. 0.005^2.
  * `lambda_B1`  A regularization parameter for the B1 sensitivity
  * `lambda_CSF` A regularization parameter for the CSF sensitivity
  * `maxMeas`   By default (BLAKJac_defaults), it is set to 4 times the maximum number of times that a specific (ky,kz)-combination will be seen during the measurement.
  * `maxstate`   the maximum number of state that the EPG-estimation of signal and derivatives will take into account
  * `nky`   By default (BLAKJac_defaults), the range of applied ky values
  * `nkz`   By default (BLAKJac_defaults), the range of applied kz values
  * `plotfuncs`   (Filled in by BLAKJac_defaults!(); do not adapt)
  * `plottypes`   An array of strings. If the array contains a recognized string, a plot is produced

| String              | description                                                                           |
|:------------------- |:------------------------------------------------------------------------------------- |
| "first"             | plots the RF shape alongside the ky and the kz of the first sample of each trajectory |
| "trajectories"      | plots the first 10 trajectories                                                       |
| "noisebars"         | a barplot of the noise levels                                                         |
| "weights"           | colorful plot of T1- and T2-sensitivities over time                                   |
| "original_jacobian" | (to be described)                                                                     |
| "noiseSpectrum"     | Graphs of noise spectral density over ky, one for T1 map and one for T2 map           |
| "infocon"           | (to be described)                                                                     |

  * `rfFile`   Text used to tag the H-matrix dictionary
  * `sigma_ref`   (used in calculating information content)
  * `startstate`   either 1 (meaning no inversion prepulse) or -1 (meaning an inversion prepulse one TR prior to actual sequence)
  * `T1ref`   The "reference" T1 value
  * `T2ref`   The "reference" T2 value
  * `T1T2set`   a set of (T1,T2) values around which BLAKJac will be evaluated. Typically "the 7-points mix" (ToDo: redesign this)
  * `TR`  in seconds
  * `useSurrogate`  should be false by default; if true, it uses a polynomial estimate of signal and derivatives, rather than the actual EPG estimate
  * `useSymmetry`   if true, it is assumed that the phase of proton density is very smooth, such that, for BLAKJac analysis, all output can be considerd to be real
