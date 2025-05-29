```
vomps!(AL1, AR1, T, AL, AR, opts)
```

MPO-MPS product compression using VOMPS algorithm. The MPO is represented by the MPO tensor T, and the MPS is represented by the left and right MPS tensors AL and AR. The output is saved in AL1 and AR1.

# Arguments

  * `AL1/AR1::MPSTensor`: Target left/right MPS tensors to update (modified in-place)
  * `T::MPOTensor`: MPO local tensor
  * `AL/AR::MPSTensor`: MPS tensors
  * `opts::VOMPSOptions`: Algorithm configuration parameters

# Returns

  * `AL1/AR1::MPSTensor`: Updated left/right MPS tensors (modified in-place)
  * `AC1::MPSTensor`: Updated center AC tensor
  * `C1::MPSBondTensor`: Updated center bond tensor
  * `power_method_conv::Real`: Convergence metric from final gauge fixing (NaN if disabled). Measures the difference between the MPSs represented by AL1 and AL (should be = 0 for equivalent MPS)
