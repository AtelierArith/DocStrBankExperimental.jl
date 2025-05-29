```
fmi3GetVariableDependencies(c::FMU3Instance, vr::Union{fmi3ValueReference, String})
```

実際の依存関係（型 dependenciesKind）は、関数 fmi3GetVariableDependencies を呼び出すことで取得できます。

# 引数

  * `c::FMU3Instance`: 引数 `c` は、FMI 3.0 標準における FMU のインスタンス化されたインスタンスを表す可変構造体です。
  * `vr::Union{fmi3ValueReference, String}`: 引数 `vr` は、問い合わせる変数を定義する「ValueReference」と呼ばれる値ハンドルです。

# 戻り値

  * `elementIndicesOfDependent::AbstractArray{Csize_t}`: 呼び出し環境によって割り当てられたサイズ `nDependencies` の size_t 値のバッファを指す必要があります。この関数によって、依存関係情報が提供される依存変数の要素インデックスで埋められます。要素インデックスは 1 から始まります。要素インデックス 0 を使用すると、変数のすべての要素を意味します。（注：配列が複数の次元を持つ場合、インデックスはセクション 2.2.6.1 で定義された値の順序と同じ順序で直列化されます。）
  * `independents::AbstractArray{fmi3ValueReference}`: 呼び出し環境によって割り当てられたサイズ `nDependencies` の `fmi3ValueReference` 値のバッファを指す必要があります。この関数によって、この依存関係エントリが依存している独立変数の値参照で埋められます。
  * `elementIndicesIndependents::AbstractArray{Csize_t}`: 呼び出し環境によって割り当てられたサイズ `nDependencies` の size_t `values` のバッファを指す必要があります。この関数によって、この依存関係エントリが依存している独立変数の要素インデックスで埋められます。要素インデックスは 1 から始まります。要素インデックス 0 を使用すると、変数のすべての要素を意味します。（注：配列が複数の次元を持つ場合、インデックスはセクション 2.2.6.1 で定義された値の順序と同じ順序で直列化されます。）
  * `dependencyKinds::AbstractArray{fmi3DependencyKind}`: 呼び出し環境によって割り当てられたサイズ `nDependencies` の dependenciesKind 値のバッファを指す必要があります。この関数によって、この依存関係エントリの依存関係を説明する列挙値で埋められます。

# 出典

  * FMISpec3.0 リンク: [https://fmi-standard.org/](https://fmi-standard.org/)
  * FMISpec3.0: 2.2.3 プラットフォーム依存定義
  * FMISpec3.0: 2.2.4 関数によって返されるステータス
  * FMISpec3.0: 2.2.10. 変数の依存関係

また、[`fmi3GetVariableDependencies!`](@ref) も参照してください。 ```
