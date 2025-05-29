```
fmi3GetVariableDependencies!(c::FMU3Instance, vr::fmi3ValueReference, elementIndiceOfDependents::AbstractArray{Csize_t}, independents::AbstractArray{fmi3ValueReference},  
    elementIndiceOfInpendents::AbstractArray{Csize_t}, dependencyKind::AbstractArray{fmi3DependencyKind}, ndependencies::Csize_t)
```

実際の依存関係（依存関係の種類）は、関数fmi3GetVariableDependenciesを呼び出すことで取得できます。

# 引数

  * `c::FMU3Instance`: 引数 `c` は、FMI 3.0標準におけるFMUのインスタンス化されたインスタンスを表す可変構造体です。
  * `vr::fmi3ValueReference`: 引数 `vr` は、問い合わせる変数を定義する「ValueReference」と呼ばれる値ハンドルです。
  * `nvr::Csize_t`: 引数 `nvr` は、`vr` のサイズを定義します。
  * `elementIndiceOfDependents::AbstractArray{Csize_t}`: 呼び出し環境によって割り当てられたサイズ `nDependencies` の size_t 値のバッファを指す必要があります。この関数によって、依存関係情報が提供される依存変数の要素インデックスで埋められます。要素インデックスは1から始まります。要素インデックス0を使用すると、変数のすべての要素を意味します。（注：配列が複数の次元を持つ場合、インデックスはセクション2.2.6.1で定義された値の順序と同じ順序で直列化されます。）
  * `independents::AbstractArray{fmi3ValueReference}`: 呼び出し環境によって割り当てられたサイズ `nDependencies` の `fmi3ValueReference` 値のバッファを指す必要があります。この関数によって、この依存関係エントリが依存している独立変数の値参照で埋められます。
  * `elementIndiceOfInpendents::AbstractArray{Csize_t}`: 呼び出し環境によって割り当てられたサイズ `nDependencies` の size_t `values` のバッファを指す必要があります。この関数によって、この依存関係エントリが依存している独立変数の要素インデックスで埋められます。要素インデックスは1から始まります。要素インデックス0を使用すると、変数のすべての要素を意味します。（注：配列が複数の次元を持つ場合、インデックスはセクション2.2.6.1で定義された値の順序と同じ順序で直列化されます。）
  * `dependencyKind::AbstractArray{fmi3DependencyKind}`: 呼び出し環境によって割り当てられたサイズ `nDependencies` の dependenciesKind 値のバッファを指す必要があります。この関数によって、この依存関係エントリの依存関係を説明する列挙値で埋められます。
  * `ndependencies::Csize_t`: 呼び出し環境が結果バッファに割り当てた依存関係の数を指定し、`fmi3GetNumberOfVariableDependencies` を呼び出すことで得られる値に対応する必要があります。

# 戻り値

  * `status::fmi3Status`: 戻り値 `status` は、`fmi3Status` 型の列挙であり、関数呼び出しの成功を示します。

詳細:

  * `fmi3OK`: すべて正常
  * `fmi3Warning`: 物事は完全に正しくないが、計算は続行できる
  * `fmi3Discard`: スレーブが通信ステップのサブインターバルのみを正常に計算した場合
  * `fmi3Error`: 通信ステップを全く実行できなかった場合
  * `fmi3Fatal`: FMUを不可逆的に破損させるエラーが発生した場合

# ソース

  * FMISpec3.0 リンク: [https://fmi-standard.org/](https://fmi-standard.org/)
  * FMISpec3.0: 2.2.3 プラットフォーム依存の定義
  * FMISpec3.0: 2.2.4 関数によって返されるステータス
  * FMISpec3.0: 2.2.10 変数の依存関係

また、[`fmi3GetVariableDependencies!`](@ref)も参照してください。
