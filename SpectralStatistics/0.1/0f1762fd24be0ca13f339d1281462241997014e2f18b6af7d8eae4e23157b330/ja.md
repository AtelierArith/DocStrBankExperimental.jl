```
unfold_spectrum(spect::DataSample, f::Function) → unfolded::UnfoldedSpectrum
```

`spect`の展開されたスペクトルを、関数`f`を用いて状態密度の滑らかな部分として返します。

## 引数

  * `spect`: 展開されるスペクトル。
  * `f(x)` : 状態密度の滑らかな部分をモデル化する関数で、引数`x`はエネルギーです。

## 戻り値

  * `unfolded` : 型[`UnfoldedSpectrum`](@ref)のインスタンスとしての展開されたスペクトル。
