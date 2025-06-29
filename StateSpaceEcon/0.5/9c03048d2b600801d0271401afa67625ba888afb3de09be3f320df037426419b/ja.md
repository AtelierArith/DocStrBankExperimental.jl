```
shockdecomp(model, plan, exog_data; control, solver, [options])
```

与えられたモデル、計画、外生（ショック）データ、および制御ソリューションのためのショック分解を計算します。

`control`オプションが指定されていない場合、モデルインスタンスに保存されている定常状態ソリューションを使用します。アルゴリズムは、`control`が指定された計画範囲と最終条件に対する動的モデルのソリューションであると仮定します。残差を検証し、警告を発しますが、これを強制することはありません。詳細は[`steadystatedata`](@ref)を参照してください。

アルゴリズムの一部として、指定された計画、データ、およびソルバーを使用してシミュレーションを実行します。シミュレーションを制御する追加オプションについては、[`simulate`](@ref)を参照してください。

[`simulate`](@ref)とは異なり、ここでは`exogdata`と`control`が`MVTSeries`であることが必要です。つまり、プレーンな`Array`や`Workspace`は許可されていません。

返される値は、3つの要素を含む`Workspace`です：`c`は`control`のコピーを含み、`s`は指定された`plan`と`exogdata`に対するシミュレーションされたソリューションを含み、`sd`はショック分解データを含みます。`sd`内のデータは、各変数のための`MVTSeries`を含む`Workspace`として整理されています。
