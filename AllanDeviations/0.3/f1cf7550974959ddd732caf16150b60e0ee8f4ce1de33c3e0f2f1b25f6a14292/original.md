mallandev(data, rate; [frequency=false], [overlapping=true], [taus=Octave]) Calculates the modified allan deviation

#parameters:

  * `<data>`:			The data array to calculate the deviation from either as as phases or frequencies.
  * `<rate>`:			The rate of the data given.
  * `[frequency]`:		True if `data` contains frequency data otherwise (default) phase data is assumed.
  * `[overlapping]`:	True (default) to calculate overlapping deviation, false otherwise.
  * `[taus]`:			Taus to calculate the deviation at. This can either be an AllanTauDescriptor type `AllTaus, Decadade, HalfDecade, Octave, HalfOctave, QuarterOctave`, an array of taus to calculate at, a float number to build a custom log-scale on or an integer to build a specific number of log spaced points.

#returns: named tupple (tau, deviation, error, count)

  * `tau`:		Taus which where used.
  * `deviation`:	Deviations calculated.
  * `error`:		Respective errors.
  * `count`:		Number of contributing terms for each deviation.
