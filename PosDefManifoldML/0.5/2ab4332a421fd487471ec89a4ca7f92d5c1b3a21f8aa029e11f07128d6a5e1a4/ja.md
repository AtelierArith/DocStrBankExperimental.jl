```julia
mutable struct MDM <: MDMmodel
    metric  :: Metric = Fisher;
    pipeline :: Pipeline
    featDim :: Int
    means   :: ℍVector
    imeans  :: ℍVector
end
```

MDM 機械学習モデルは、この可変構造体にカプセル化されています。MDM モデルには、`.metric`、`.pipeline`、`.featDim`、および `.means` の 4 つのフィールドがあります。

フィールド `metric` は、ユーザーによって指定される型 [Metric](https://marco-congedo.github.io/PosDefManifold.jl/dev/MainModule/#Metric::Enumerated-type-1) です。これは、クラスの平均と平均への距離を計算するために採用されるメトリックです。

他のすべてのフィールドは、デフォルトの作成者によってモデルの作成時に渡される引数には対応していません。代わりに、モデルが [`fit`](@ref) 関数によって作成されるときに後で埋められます。

フィールド `pipeline` は、データに適用されるオプションのデータ前処理器のシーケンスを保持する型 [`Pipeline`](@ref) です。パイプラインは、ML モデルがフィットされるときに学習され、モデルに保存されます。パイプラインがフィットされると、[`predict`](@ref) 関数の各呼び出し時にデータに自動的に適用されます。

フィールド `featDim` は、モデルが作用する多様体の次元です。これは *n(n+1)/2* で与えられ、*n* は PD 行列の次元です。このフィールドはユーザーによって指定されるべきではなく、代わりに MDM モデルが [`fit`](@ref) 関数を使用してフィットされるときに計算され、その後のみアクセス可能です。

フィールド `means` は、クラスの平均を保持する [ℍVector](https://marco-congedo.github.io/PosDefManifold.jl/dev/MainModule/#%E2%84%8DVector-type-1) です。すなわち、各クラスの平均が 1 つずつあります。このフィールドはユーザーによって指定されるべきではなく、代わりに MDM モデルが [`fit`](@ref) 関数を使用してフィットされるときに計算され、その後のみアクセス可能です。

フィールド `imeans` は、`means` の行列の逆を保持する ℍVector です。これもユーザーによって指定されるべきではなく、モデルがフィットされるときに計算され、その後のみアクセス可能です。これは、モデルがフィッシャーメトリック（デフォルト）を使用してフィットされている場合に、距離の計算を最適化するために使用されます。

**例**:

```julia
using PosDefManifoldML, PosDefManifold

# 空のモデルを作成
m = MDM(Fisher)

# フィッシャーメトリックがデフォルトメトリックであるため、
# これは次のように等価です
m = MDM()
```

一般に、空の MDM モデルが関数への引数として必要な場合にのみ、これらのコンストラクタを呼び出す必要があることに注意してください。そうでない場合は、[`fit`](@ref) 関数を使用して MDM モデルをより簡単に作成してフィットさせることができます。
