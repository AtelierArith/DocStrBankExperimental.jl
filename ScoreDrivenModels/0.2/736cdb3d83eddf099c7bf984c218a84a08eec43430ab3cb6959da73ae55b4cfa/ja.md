```
ScoreDrivenModel
```

スコア駆動モデルのコンストラクタ。モデルはラグ構造、分布、およびスケーリングを受け取ります。ラグ構造は、整数 `p` と `q` を渡して `1` から `p` まで、`1` から `q` までのすべてのラグを追加するか、または希望するラグを含む整数のベクトル `ps` と `qs` を渡すことで、2つの異なる方法で定義できます。モデルを構築すると、推定が必要なすべての未知のパラメータは `NaN` として表されます。

```jldoctest
# p と q を渡す
julia> ScoreDrivenModel(2, 2, LogNormal, 0.5)
ScoreDrivenModel{LogNormal,Float64}([NaN, NaN], Dict(2=>[NaN 0.0; 0.0 NaN],1=>[NaN 0.0; 0.0 NaN]), Dict(2=>[NaN 0.0; 0.0 NaN],1=>[NaN 0.0; 0.0 NaN]), 0.5)

# ps と qs を渡す
julia> ScoreDrivenModel([1, 12], [1, 12], Gamma, 0.0)
ScoreDrivenModel{Gamma,Float64}([NaN, NaN], Dict(12=>[NaN 0.0; 0.0 NaN],1=>[NaN 0.0; 0.0 NaN]), Dict(12=>[NaN 0.0; 0.0 NaN],1=>[NaN 0.0; 0.0 NaN]), 0.0)
```

すべてのパラメータを時間変動と見なしたくない場合は、キーワード引数 `time_varying_params` を通じて表現できます。そこには、どのパラメータが時間変動であるべきかを表す数を含むベクトルを渡す必要があります。例えば、正規分布において `time_varying_params = [1]` は、$\mu$ のみが時間変動であることを示します。辞書（番号 => パラメータ）の表は、セクション [ScoreDrivenModels distributions](@ref) にあります。

```jldoctest
julia> ScoreDrivenModel([1, 12], [1, 12], Normal, 1.0; time_varying_params = [1])
ScoreDrivenModel{Normal,Float64}([NaN, NaN], Dict(12=>[NaN 0.0; 0.0 0.0],1=>[NaN 0.0; 0.0 0.0]), Dict(12=>[NaN 0.0; 0.0 0.0],1=>[NaN 0.0; 0.0 0.0]), 1.0)
```
