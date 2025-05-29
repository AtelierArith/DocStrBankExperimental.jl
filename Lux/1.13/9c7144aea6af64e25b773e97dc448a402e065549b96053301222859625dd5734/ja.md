```
Parallel(connection, layers...; name=nothing)
Parallel(connection; name=nothing, layers...)
Parallel(; connection, layers..., name=nothing)
```

各パスに入力を渡し、その出力を `connection` で減少させるレイヤーを作成します。

## 引数

  * `connection`: 入力を各レイヤーを通過させた後に呼び出される `N` 引数関数。`connection = nothing` の場合、`Parallel(nothing, f, g)(x, y) = (f(x), g(y))` を返します。
  * レイヤーは2つの形式で指定できます：

      * `N` 個の Lux レイヤーのリスト
      * `N` のキーワード引数として指定。

# 拡張ヘルプ

## 入力

  * `x`: `x` がタプルでない場合、戻り値は `connection([l(x) for l in layers]...)` として計算されます。そうでない場合は、各レイヤーに1つずつ渡され、したがって `Parallel(+, f, g)(x, y) = f(x) + g(y)` となります。

## 戻り値

  * 出力がどのように計算されるかは入力セクションを参照してください。
  * `layers` の更新された状態

## パラメータ

  * 各 `layer` のパラメータは、`fields = layer_1, layer_2, ..., layer_N` の NamedTuple にラップされています（kwargs API を使用する場合、名前が変更されます）。

## 状態

  * 各 `layer` の状態は、`fields = layer_1, layer_2, ..., layer_N` の NamedTuple にラップされています（kwargs API を使用する場合、名前が変更されます）。

[`SkipConnection`](@ref) も参照してください。これは1つのアイデンティティを持つ `Parallel` です。

## 例

```jldoctest
julia> model = Parallel(nothing, Dense(2, 1), Dense(2, 1))
Parallel(
    layer_1 = Dense(2 => 1),            # 3 パラメータ
    layer_2 = Dense(2 => 1),            # 3 パラメータ
)         # 合計: 6 パラメータ、
          #        さらに 0 状態。

julia> using Random;
       rng = Random.seed!(123);
       ps, st = Lux.setup(rng, model);
       x1 = randn(rng, Float32, 2);
       x2 = randn(rng, Float32, 2);

julia> size.(first(model((x1, x2), ps, st)))
((1,), (1,))
```
