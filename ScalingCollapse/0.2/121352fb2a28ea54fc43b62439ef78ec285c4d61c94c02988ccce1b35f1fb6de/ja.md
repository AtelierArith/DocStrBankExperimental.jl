```
ScalingFunction(preset::Symbol; kwargs...)
ScalingFunction(f::Function; kwargs...)
```

`ScalingFunction`は`ScalingProblem`でデータを再スケールするために使用されます。これは関数`f`とパラメータ名のセット`p_names`によって定義されます。関数`f`はデータ`d`とパラメータ`p1`、`p2`、...を引数に呼び出され、新しい`Data`オブジェクトを返します。

# 引数

  * `preset::Symbol`: `ScalingFunction`のためのプリセット。以下の`Presets`を参照してください。
  * `f::Function`: `ScalingFunction`で使用される関数`f`。カスタム`ScalingFunction`を作成するためにこの引数を渡します。fは`Data`オブジェクトとパラメータのセット`p1`、`p2`、...を受け取り、新しい`Data`オブジェクトを返す必要があります: f(d::Data, p1, p2, ...) -> Data。

    "固定パラメータ"機能を使用するために、関数`f`をキーワード引数として設定することをお勧めします（下記参照）。

# プリセット

`preset`引数は、プリセット関数`f`とプリセットのパラメータ名のセット`p_names`を使用して`ScalingFunction`を作成するために使用できます。以下のプリセットが利用可能です：

  * `:x` データのx値をx -> (x - p1)/p1 * L^(1/p2)に従って再スケールします。
  * `:xy` データのxおよびy値をx -> (x - p1)/p1 * L^(1/p2)およびy -> y * L^(p3/p2)に従って再スケールします。
  * `:xny` データのxおよびy値をx -> (x - p1)/p1 * L^(1/p2)およびy -> y * L^(-p3/p2)に従って再スケールします。

# キーワード引数

  * `p_names::Vector{String}`: `ScalingFunction`で使用されるパラメータ名`p_names`。このkwargはプリセットのパラメータ名`p_names`（p1、p2、...）を上書きするために使用できます。
  * `f::Function`: `ScalingFunction`で使用される関数`f`。このkwargはプリセット関数`f`を上書きするために使用できます。fを引数ではなくkwargとして渡すと、"固定パラメータ"機能を使用できます（下記参照）。その場合、関数fのパラメータの数はプリセットと一致する必要があります。つまり、関数fが2つのパラメータを取る場合はプリセット`:x`を使用し、3つのパラメータを取る場合はプリセット`:xy`を使用する必要があります。
  * `x_scale::String`: x値のスケーリング関数。これはプロットやJuliaの表示関数でスケーリング関数を表示するために使用されます。
  * `y_scale::String`: y値のスケーリング関数。これはプロットやJuliaの表示関数でスケーリング関数を表示するために使用されます。
  * `p::Float64`: パラメータを値に固定します。スケーリングパラメータの解析値がわかっている場合は、この値に固定することをお勧めします。これにより最適化が速くなり、より良い結果が得られる可能性があります。注意：`p`は"p1"、"p2"、...または`p_names`で指定した名前のいずれかです。

    この機能はプリセットのいずれかを使用している場合にのみ利用可能です。`f`をkwargとして設定することで、スケーリング関数を変更することはできます。

# 例

### プリセット

```julia
# x軸のみを再スケール
ScalingFunction(:x; p_names=["T_c", "nu"])

# nuを1.0に固定しましょう
ScalingFunction(:x; p_names=["T_c", "nu"], nu=1.0)

# x軸とy軸を再スケール
ScalingFunction(:xy; p_names=["T_c", "nu", "beta"])

# yに負の指数を持つx軸とy軸を再スケール
ScalingFunction(:xny; p_names=["T_c", "nu", "gamma"])
```

### カスタムスケーリング関数

```julia
# データをスケールする関数を定義
function myfunction(d::ScalingCollapse.Data, p1, p2)

    # スケールデータ用の配列を初期化
    xs = zeros(length(d.xs))
    ys = zeros(length(d.ys))
    es = zeros(length(d.es))

    # p1とp2に従ってデータをスケール
    for (i, x, y, e) in zip(eachindex(d.xs), d.xs, d.ys, d.es)
        xs[i] = (x - p1) / p1 * log(d.L)
        ys[i] = y * d.L^(p2)
        es[i] = e * d.L^(p2)
    end

    # スケールデータを持つ新しいDataオブジェクトを作成
    return ScalingCollapse.Data(d.L, xs, ys, es)
end

ScalingFunction(myfunction; p_names=["myp1", "myp2"])

# 例えば、パラメータ"myp1"を1.0に固定したいとしましょう
# プリセット:xを使用し（2つのパラメータもあるため）、関数fを上書きします
ScalingFunction(:x; f=myfunction, p_names=["myp1", "myp2"], myp1=1.0)
```
