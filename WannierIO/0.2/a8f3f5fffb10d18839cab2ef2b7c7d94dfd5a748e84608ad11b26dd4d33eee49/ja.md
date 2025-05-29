```julia
write_w90_wsvec(
    filename;
    Rvectors,
    n_wann,
    Tvectors,
    Tdegens,
    header
)

```

`prefix_wsvec.dat`を書き込みます。

# キーワード引数

  * `n_wann`: Wigner-Seitz Rvectorsの場合、Wannier関数の数のために`n_wann`を提供する必要があります。MDRS Rvectorsの場合、`n_wann`はオプションであり、`Tvectors`から自動的に決定できます。
  * `Tvectors`と`Tdegens`: 提供される場合、MDRS形式で書き込みます。そうでない場合、Wigner-Seitz形式で書き込みます。

また、[`read_w90_wsvec`](@ref)の戻り値も参照してください。
