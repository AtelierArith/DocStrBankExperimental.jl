```
χ(::SpinChannel, atom::HubbardAtom, m::BosonicFreq)
chi(::SpinChannel, atom::HubbardAtom, m::BosonicFreq)
```

Sum over all fermionic frequencies of the susceptibility, i.e. `-sum(χ(r, atom, (n, n´, m)) for n in -∞:+∞, n´ in -∞:+∞) * atom.beta^2/2 * tanh(atom.U * atom.beta / 4)^2`. This is an original calculation.
