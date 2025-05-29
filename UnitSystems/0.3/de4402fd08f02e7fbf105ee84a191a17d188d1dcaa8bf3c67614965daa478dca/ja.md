```
RankineSystem(U::UnitSystem,l,m,g0=𝟏)
```

新しい `UnitSystem` を `U` から長さと質量に沿ってスケール変更し、技術的および工学的単位を定義するために使用されるオプションの重力基準定数を持ちます。

```Julia
EntropySystem(U,𝟏,l,m,°R,vacuumpermeability(U)/m/l/g0,kilo*molarmass(U),g0)
```

例: `FPS`, `British`, `IPS`, `English`, `Survey`。
