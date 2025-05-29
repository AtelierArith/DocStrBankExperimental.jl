```
product_peps(peps_args...; unitcell=(1, 1), noise_amp=1e-2, state_vector=nothing)
```

ノイズを持つ正規化されたランダムなプロダクトPEPSを初期化します。与えられた引数は`InfinitePEPS`コンストラクタに渡されます。

ノイズの強度は`noise_amp`で調整できます。プロダクト状態の係数は、PEPSの物理的次元に一致するベクトルを含む`unitcell`サイズの行列の形で`state_vector`キーワード引数を使用して指定できます。`nothing`が提供された場合、ランダムなガウス係数が使用されます。
