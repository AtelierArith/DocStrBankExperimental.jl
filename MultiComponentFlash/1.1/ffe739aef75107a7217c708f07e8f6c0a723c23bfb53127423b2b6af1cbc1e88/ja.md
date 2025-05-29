```
flash_storage(eos, [c]; <keyword arguments>)
```

`flash_2ph!`のためのストレージを事前に割り当てます。

# 引数

  * `eos`: フラッシュに使用する状態方程式
  * `c`: 混合物の条件。条件の型は後の使用に一致する必要があります（例：ForwardDiffでの使用のため）。

# キーワード引数

  * `method = SSIFlash()`: 使用するフラッシュメソッド。`SSIFlash()`, `NewtonFlash()`または`SSINewtonFlash()`のいずれかです。
  * `static_size = false`: 高速フラッシュのために`SArrays`と`MArrays`を使用しますが、コンパイル時間は遅くなります。
  * `inc_jac`: ニュートン/ヤコビ行列のためのストレージを割り当てます。ニュートンには必要で（そのメソッドのデフォルトは`true`）、`diff_externals`のためにも必要です。
  * `diff_externals = false`: `set_partials`を使用してフラッシュの偏微分を生成するために必要な行列の逆行列のためのストレージを割り当てます。

参照: [`flash_2ph!`](@ref) [`set_partials`](@ref)
