```
χ₀(::SpinChannel, at::HubbardAtom, (n, n´, m)::FermiFermiBose)
χ₀(::SpinChannel, at::HubbardAtom, (n, m)::Tuple{FermionicFreq, BosonicFreq})
chi0(::SpinChannel, at::HubbardAtom, (n, n´, m)::FermiFermiBose)
chi0(::SpinChannel, at::HubbardAtom, (n, m)::Tuple{FermionicFreq, BosonicFreq})
```

ベア一般化感受性。2周波数および3周波数のバージョンは `β * χ₀(r, at, (n, m)) = sum(χ₀(r, at, (n, n´, m)) for n´ in -∞:+∞)` によって関連しています。(式 6)
