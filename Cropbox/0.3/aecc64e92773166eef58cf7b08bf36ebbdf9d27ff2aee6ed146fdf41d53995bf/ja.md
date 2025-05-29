```
evaluate(S, obs; <キーワード引数>) -> 数値 | タプル
```

指定されたシステム `S` と観測データ `obs` のシミュレーション結果の出力を評価指標の選択とともに比較します。

# 引数

  * `S::Type{<:System}`: 評価されるシステムの型。
  * `obs::DataFrame`: 評価に使用される観測データ。

# キーワード引数

## 設定

  * `config=()`: システムの単一設定（`configs` と一緒には使用できません）。
  * `configs=[]`: システムの複数設定（`config` と一緒には使用できません）。

## レイアウト

  * `index=nothing`: 出力のインデックス列を構成する変数；デフォルトは `context.clock.time` にフォールバックします。
  * `target`: 出力の非インデックス列を構成する変数。

## 評価

  * `metric=nothing`: 評価指標（`:rmse`, `:nrmse`, `:mae`, `:mape`, `:ef`, `:dr`）；デフォルトは RMSE です。

残りのキーワード引数は、システム `S` の実行に関して `simulate` に渡されます。

参照: [`simulate`](@ref), [`calibrate`](@ref), [`@config`](@ref)

# 例

```julia-repl
julia> @system S(Controller) begin
           a => 19 ~ preserve(u"m/hr", parameter)
           b(a) ~ accumulate(u"m")
       end;

julia> obs = DataFrame(time=10u"hr", b=200u"m");

julia> configs = @config !(:S => :a => [19, 21]);

julia> evaluate(S, obs; configs, target=:b, stop=10u"hr")
10.0 m
```
