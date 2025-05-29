```
χ(::SpinChannel, atom::HubbardAtom, m::BosonicFreq)
chi(::SpinChannel, atom::HubbardAtom, m::BosonicFreq)
```

感受性のすべてのフェルミ周波数にわたる合計、すなわち `-sum(χ(r, atom, (n, n´, m)) for n in -∞:+∞, n´ in -∞:+∞) * atom.beta^2/2 * tanh(atom.U * atom.beta / 4)^2`。これはオリジナルの計算です。
