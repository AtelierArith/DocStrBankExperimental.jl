```julia
dataProtocol(paper)

```

Structure to describe a plasticity protocol "conoc"

# Arguments

  * `paper` can be `["oconnor", "Bittner", "Goldings01", "Buchenan", "Tigaret_jitter_timespent", "Tigaret_jitter_double_1", "Poisson", "Tigaret_jitter", "Dudek_jitter", "TigaretMellor16", "TigaretMellor16_poisson", "Sleep_age", "Poisson_physiological_range", "YannisDebanne20_freq", "YannisDebanne20_freq_delay", "YannisDebanne20_ratio", "YannisDebanne20_inv", "Tigaret_burst", "Tigaret_burst_temp", "Tigaret_burst_age", "Tigaret_burst_freq", "Tigaret_burst_ca", "Tigaret_burst_dist", "Tigaret_freq_1200", "Tigaret_tripost", "Tigaret_preburst", "Tigaret_single", "TigaretMellor_sparse", "TigaretMellor_jitter_sparse", "DudekBear92-BCM-Ca", "DudekBear92-BCM", "DudekBear92-BCM-900", "DudekBear92-BCM-37", "DudekBear92-BCM-33", "DudekBear92-BCM-priming", "DudekBear92_timespend", "DudekBear92-100", "DudekBear_short", "FujiBito", "DudekBear92-sliding", "DudekBear92_temp", "DudekBear92_Ca", "DudekBear92_Mg", "DudekBear92_dist", "DudekBear92-Age", "Blocking_age_control", "Blocking_yNMDA", "Blocking_oNMDA", "Blocking_yBaP", "Blocking_oBaP", "Blocking_yGABA", "Blocking_oGABA", "DudekBear92_BCM_recovery", "DudekBear93-LFS", "DudekBear93-TBS", "Cao-TBS", "RecoverLTD", "Chang19", "Fujii_CaN", "YannisDebanne20", "YannisDebanne_temp", "YannisDebanne_age", "Meredith03-GABA", "TigaretvsMeredith", "YannisvsMeredith", "WittenbergWang06_D", "WittenbergWang06_B", "WittenbergWang06_P", "Mizuno01-LTP-Mg", "Mizuno01LTP", "Mizuno01LTD"]`
  * `n_pre` number of presynaptic pulses
  * `delay_pre` delay between presynaptic pulses
  * `n_pos` number of postsynaptic pulses
  * `delay_pos` delay between postsynaptic pulses
  * `delay` delay between pre and postsynaptic spikes (used in STDP)
  * `pulse` number of pulses/pairing repetitions
  * `freq` frequency
  * `causal` causal inverts the order of pre and post, uses true or false
  * `protocol` name of the protocol
  * `weight` info entry with weight change value (not used in the model)
  * `outcome` `String` to show the qualitative outcome (not used in the model)
  * `paper` paper is a `String` to choose a predefined protocol (e.g. paper = TigaretMellor16)
  * `temp` temperature by which all temperature-sensitive mechanisms will be adapted
  * `injection` (nA) current injected in the soma, used to make postsynaptic spikes (BaPs)
  * `exca` (μM) extracellular calcium, we expressed it in μM to be used in the ghk function
  * `exmg` (mM) extracellular magnesium, we expressed it in mM, however, it is converted to μM in the magnesium relief function
  * `repeat_times` number of epochs additional epochs to include, for instance, TBS is usually expressed in epochs
  * `repeat_after` time difference between the epochs (ms)
  * `testing_freq` some protocols use test frequencies, this can be useful to evaluate the effect or absence of it, or to add a regular background presynaptic stimuli. 0 Hz will turn it off
  * `inj_time` duration (ms) of the current injection to elicit a BaP
  * `age` animal age (rat)
  * `AP_by_EPSP` `yes` or `no`, to let additional BaPS induced by EPSPs to be included in the stimulation
  * `GABA_block` `yes` or `no` GABAr conductance is set zero
  * `jitter` standard deviation of a Gaussian used to jitter the spikes
  * `sparse` percentage of spikes skipped
  * `dista` distance from the soma in μm
