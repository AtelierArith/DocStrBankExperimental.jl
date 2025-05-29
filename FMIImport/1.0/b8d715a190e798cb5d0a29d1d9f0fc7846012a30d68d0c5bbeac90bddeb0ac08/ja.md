```
fmi3GetNumberOfVariableDependencies(c::FMU3Instance, vr::fmi3ValueReference, nvr::Ref{Csize_t})
```

与えられた変数の依存関係の数は、構造パラメータが変更された場合に変わる可能性があり、fmi3GetNumberOfVariableDependenciesを呼び出すことで取得できます。

この情報は、ModelDescriptionの'providesPerElementDependencies'タグが設定されている場合にのみ取得できます。

# 引数

  * `c::FMU3Instance`: 引数 `c` は、FMI 3.0標準におけるFMUのインスタンス化されたインスタンスを表す可変構造体です。
  * `vr::Union{fmi3ValueReference, String}`: 引数 `vr` は、照会される変数を定義する「ValueReference」と呼ばれる値ハンドルです。

# 戻り値

  * `size::Integer`: 戻り値 `size` は、与えられた変数の依存関係の数です。

# 出典

  * FMISpec3.0 リンク: [https://fmi-standard.org/](https://fmi-standard.org/)
  * FMISpec3.0: 2.2.3 プラットフォーム依存の定義
  * FMISpec3.0: 2.2.10. 変数の依存関係

他にも [`fmi3GetNumberOfVariableDependencies`](@ref) を参照してください。
