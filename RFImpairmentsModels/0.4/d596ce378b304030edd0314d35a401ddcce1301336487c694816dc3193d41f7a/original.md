Adding Carrier Frequency Offset δ in Hz to the input signal x sampled at frequency fs (In Hz) with initial phase ϕ (default 0)
This function does not mutate the input signal. See addCFO! for mutating function. In case you want to add normalized CFO, set the fs to 1. 
y = addCFO(x,δ,fs,ϕ=0) 
Input Parameters 

  * x : Input signal
  * δ : Carrier frequency offset [Hz]
  * fs : Sampling rate [Hz]
  * ϕ : Offset phase (Default 0) [Hz]

Output parameters 

  * y : Signal with CFO

There are 3 versions 

  * One with allocation on the output y = addCFO(x,δ,fs,ϕ) or y = addCFO(x,cfo::CFO)
  * One without allocation and mutation of first input : addCFO!(y,x,...)
  * One with in place location of input addCFO!(x,...)
