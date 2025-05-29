変数から基本的なNaN値を返すヘルパー関数で、他の変数を作成する際に使用します。特に、2つのモデル引数を取り、それらの引数の両方と互換性のある新しい変数を作成するのに便利です。これは、デフォルト値のない変数を示すためにNaNで埋められた値を返す点で`compatible_values`とは異なります。

```julia
compatible_shape(x,y)
compatible_shape(x)
```

まだいくつかの問題がありますが、基本的なケースでは機能します。現在は型の昇格は行われていません。

### 引数

  * `x`, `y` : オブジェクトまたは変数

### 戻り値

返されるオブジェクトは、`x`と`y`の両方に共通する型と長さのNaNを持っています。

### 例

```julia
a = Unknown(45.0 + 10im)
x = Unknown(compatible_shape(a))   # NaN + NaNimで初期化されます。
a = Unknown()
b = Unknown([1., 0.])
y = Unknown(compatible_shape(a,b)) # [NaN, NaN]で初期化されます。
```
