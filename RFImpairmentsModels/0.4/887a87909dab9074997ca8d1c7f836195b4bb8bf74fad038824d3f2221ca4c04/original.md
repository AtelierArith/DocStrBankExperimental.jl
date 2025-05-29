Apply Power Amplifier non linearity to input signal `x` following non linear PA model defined in structure `pa` There are 3 version 

  * One with allocation of the output y = addNonLinearPA(x,pa)
  * One with in place mutation of the first input addNonLinearPA!(y,x,pa)
  * One with in place mutation of the input signal addNonLinearPA!(x,pa)
