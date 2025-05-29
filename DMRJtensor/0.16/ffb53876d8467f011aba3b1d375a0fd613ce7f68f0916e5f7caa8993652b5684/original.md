```
qmps = MPS(Qlabels,arr[,oc=1,newnorm=true,setflux=false,flux=...,randomize=true,override=true,lastfluxzero=false])
```

Converts an array `arr` into a quantum number MPS `qmps` with quantum numbers assigned from an array of `qnum` vectors `Qlabels`

# Optional arguments

  * `mps::MPS`: dense MPS
  * `Qlabels::Array{Array{Qnum,1},1}`: quantum number labels on each physical index (assigns physical index labels mod size of this vector)
  * `oc::Integer`: Integer
  * `newnorm::Bool`: set new norm of the MPS tensor
  * `setflux::Bool`: toggle to force this to be the total flux of the MPS tensor
  * `flux::Qnum`: quantum number to force total MPS flux to be if setflux=true
  * `randomize::Bool`: randomize last tensor if flux forces a zero tensor
  * `lastfluxzero::Bool`: determines whether the rightmost flux should be zero or not
