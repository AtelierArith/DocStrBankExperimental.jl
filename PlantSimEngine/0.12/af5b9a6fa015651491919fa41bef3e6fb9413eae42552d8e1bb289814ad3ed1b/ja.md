```
fit()
```

測定値と（潜在的に）初期化値を使用してモデルのパラメータを最適化します。

モデラーは、次のデザインパターンに従って、自分のモデルのために `fit` メソッドを実装する必要があります。

関数への呼び出しは、最初の引数としてモデルタイプを取るべきです（T::Type{<:AbstractModel}）、データを2番目の引数として取ります（`Table.jl` 互換の型、例えば `DataFrame`）、およびパラメータの初期化をキーワード引数として取ります（必要に応じてデフォルト値を持つ）。

例えば、例のスクリプトからの `Beer` モデルのフィッティングメソッドは次のようになります（`src/examples/Beer.jl` を参照）：

```julia
function PlantSimEngine.fit(::Type{Beer}, df; J_to_umol=PlantMeteo.Constants().J_to_umol)
    k = Statistics.mean(log.(df.Ri_PAR_f ./ (df.PPFD ./ J_to_umol)) ./ df.LAI)
    return (k=k,)
end
```

この関数は、最適化されたパラメータを `(parameter_name=parameter_value,)` の形式の `NamedTuple` として返すべきです。

以下は、`PPFD`、`LAI` および `Ri_PAR_f` の「測定値」から `k` パラメータをフィットさせる `Beer` モデルの使用例です。

```julia
# 例のプロセスとモデルを含める:
using PlantSimEngine.Examples;

m = ModelList(Beer(0.6), status=(LAI=2.0,))
meteo = Atmosphere(T=20.0, Wind=1.0, P=101.3, Rh=0.65, Ri_PAR_f=300.0)
run!(m, meteo)
df = DataFrame(aPPFD=m[:aPPFD][1], LAI=m.status.LAI[1], Ri_PAR_f=meteo.Ri_PAR_f[1])
fit(Beer, df)
```

これはフィッティングメソッドが機能することを示すためのダミー例であることに注意してください。PPFDを `k=0.6` の値でビール・ランバートの法則を使用してシミュレートし、その後シミュレートされたPPFDを使用して再度 `k` パラメータをフィットさせると、シミュレーションで使用されたのと同じ値が得られます。
