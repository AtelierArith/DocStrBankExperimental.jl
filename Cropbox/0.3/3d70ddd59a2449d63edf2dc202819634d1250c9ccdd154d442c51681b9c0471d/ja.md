```
calibrate(S, obs; <キーワード引数>) -> Config | OrderedDict
```

与えられたシステム `S` のパラメータセットを取得し、提供された観測 `obs` にできるだけ近いシミュレーションを行います。異なるパラメータセットの組み合わせで多数のシミュレーションが実施され、評価指標の選択に基づいて最適なものが選ばれます。内部的には、BlackboxOptim.jl の差分進化アルゴリズムが使用されます。

# 引数

  * `S::Type{<:System}`: キャリブレーションされるシステムのタイプ。
  * `obs::DataFrame`: キャリブレーションに使用される観測データ。

# キーワード引数

## 設定

  * `config=()`: システムの単一の基本設定（`configs` と一緒には使用できません）。
  * `configs=[]`: システムの複数の基本設定（`config` と一緒には使用できません）。

## レイアウト

  * `index=nothing`: 出力のインデックス列を構成する変数；デフォルトは `context.clock.time` に戻ります。
  * `target`: 出力の非インデックス列を構成する変数。

## キャリブレーション

  * `parameters`: キャリブレーションされる境界値の範囲を持つパラメータ。
  * `metric=nothing`: 評価指標（`:rmse`, `:nrmse`, `:mae`, `:mape`, `:ef`, `:dr`）；デフォルトは RMSE。

## マルチオブジェクティブ

  * `weight=nothing`: 複数のターゲットをキャリブレーションするための重み；デフォルトは等しい重みを仮定します。
  * `pareto=false`: 複数のターゲットを満たす単一の解の代わりにパレートフロンティアを含む辞書を返します。

## 高度な

  * `optim=()`: `BlackBoxOptim.bboptimize` のための追加オプション。

残りのキーワード引数は、システム `S` を実行する際に `simulate` に渡されます。

参照: [`simulate`](@ref), [`evaluate`](@ref), [`@config`](@ref)

# 例

```julia-repl
julia> @system S(Controller) begin
           a => 0 ~ preserve(parameter)
           b(a) ~ accumulate
       end;

julia> obs = DataFrame(time=10u"hr", b=200);

julia> p = calibrate(S, obs; target=:b, parameters=:S => :a => (0, 100), stop=10)
...
Config for 1 system:
  S
    a = 20.0
```
