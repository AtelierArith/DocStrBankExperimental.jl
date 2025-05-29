```
freedom(T::Real,G::AbstractMole) = 2heatvolume(T,G)/gasconstant(G)
```

自由度 `f` は、モルあたりの蓄積エネルギー `gasconstant(G)*T/2`（無次元）です。
