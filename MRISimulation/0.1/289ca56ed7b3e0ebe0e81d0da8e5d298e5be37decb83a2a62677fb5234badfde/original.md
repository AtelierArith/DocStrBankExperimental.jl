## General Multi-Echo sequence with variable flip angles and TR.

The phase of the excitation pulse has a phase of -90° in order to fulfill CPMG conditions.

For simplicity instantaneous pulses are assumed.

echoes apperat at times T*echo, 2*T*echo,..., numContrasts*T_echo after the excitation pulse

# Fields

  * `excitationAngle::Float64`            - flip angle of the excitation pulse
  * `refocusingAngles :: Vector{Float64}` - flip angles of the refocusing pulses
  * `T_rf::Vector{Float64}`               - times of the refocusing pulses relative to the excitation pulse
  * `T_echo:: Vector{Float64}`            - echo times relative to the excitation pulse
