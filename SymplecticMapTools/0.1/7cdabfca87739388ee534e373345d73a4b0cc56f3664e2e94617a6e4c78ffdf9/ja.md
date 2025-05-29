```
doubling_birkhoff_average(h::Function, F::Function, x0::AbstractVector;
                          tol::Number = 1e-10, T_init::Integer=10,
                          T_max::Integer=320)
```

可観測関数 `h` の重み付きビルコフエルゴード平均を、マップ `F` の軌道に沿って適応的に求めます。

引数:

  * `h`: Rᵈ から Rⁿ への関数で、d は状態空間の次元、n は観測の次元です
  * `F`: (シンプレクティック) マップ: Rᵈ から Rᵈ への関数
  * `x0`: Rᵈ における軌道の初期点
  * `tol`: 収束が判断される許容誤差。平均が倍増の間に `tol` よりも変化しない場合、関数は返します
  * `T_init`: 考慮される軌道の初期長さ
  * `T_max`: 考慮される最大軌道長さ

出力:

  * `ave`: 軌道に沿った `h` の平均
  * `xs`: 軌道
  * `hs`: 軌道上の `h` の値
  * `conv_flag`: 平均が収束した場合は `true`
