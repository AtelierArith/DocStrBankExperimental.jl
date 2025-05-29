変数から基本値を返すヘルパー関数で、他の変数を作成する際に使用します。特に、2つのモデル引数を取り、それらの引数の両方に互換性のある新しい変数を作成するのに便利です。

```julia
compatible_values(x,y)
compatible_values(x)
```

まだ多少壊れていますが、基本的なケースでは機能します。現在は型の昇格は行われていません。

### 引数

  * `x`, `y` : オブジェクトまたは変数

### 戻り値

返されるオブジェクトは、`x` と `y` の両方に共通する型と長さのゼロを持っています。

### 例

```julia
a = Unknown(45.0 + 10im)
x = Unknown(compatible_values(a))   # 0.0 + 0.0imで初期化されます。
a = Unknown()
b = Unknown([1., 0.])
y = Unknown(compatible_values(a,b)) # [0.0, 0.0]で初期化されます。
```
