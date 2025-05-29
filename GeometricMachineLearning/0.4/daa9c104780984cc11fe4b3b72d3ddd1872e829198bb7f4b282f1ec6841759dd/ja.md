```
DataLoader(data::AbstractArray{<:Number, 3})
```

テンソル形式のデータに対してDataLoaderのインスタンスを作成します。

# 引数

2つのオプションのキーワード引数があります：

  * `autoencoder = false` と
  * `suppress_info = false`。

デフォルトでは、データは `TimeSeries` 型として保存されます。データを使って[`AutoEncoder`](@ref)をトレーニングしたい場合は、次のように呼び出します：

```julia
    DataLoader(data; autoencoder = true)
```

デフォルトは `autoencoder = false` と同等です。

デフォルトでは次のようになります：

```jldoctest
using GeometricMachineLearning

data = [ 1;  2;  3;; 
         4;  5;  6;;;
         7;  8;  9;; 
        10; 11; 12]

DataLoader(data)

# 出力

┌ Info: あなたは入力として3つの軸を持つテンソルを提供しました。それは次のように解釈されます：
└  (i) システム次元、(ii) 時間ステップの数、(iii) パラメータの数。
DataLoader{Int64, Array{Int64, 3}, Nothing, :TimeSeries}([1 4; 2 5; 3 6;;; 7 10; 8 11; 9 12], nothing, 3, 2, 2, nothing, nothing)
```

しかし、次のように書くと

```jldoctest
using GeometricMachineLearning

data = [ 1;  2;  3;; 
         4;  5;  6;;;
         7;  8;  9;; 
        10; 11; 12]

DataLoader(data; suppress_info = true)

# 出力

DataLoader{Int64, Array{Int64, 3}, Nothing, :TimeSeries}([1 4; 2 5; 3 6;;; 7 10; 8 11; 9 12], nothing, 3, 2, 2, nothing, nothing)
```

`@info` ステートメントは印刷されません。
