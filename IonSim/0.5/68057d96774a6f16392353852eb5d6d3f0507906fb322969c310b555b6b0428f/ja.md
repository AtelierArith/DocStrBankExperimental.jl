```
bgradient!(
        T::Chamber, ion_indxs::Tuple{Int,Int}, transition::Tuple, d::Real
    )
```

同種の2つのイオンの`transition`間にデチューニング`d`を達成するために、Bフィールドの勾配をその場で設定します。`ion_indxs`はチェーン内のイオンの順序を指します。
