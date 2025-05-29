```
RecoPlan{T <: Union{AbstractImageReconstructionParameters, AbstractImageReconstructionAlgorithm}}
```

画像再構成アルゴリズムまたはタイプ `T` のパラメータのための構成テンプレート。 `RecoPlan{T}` は、プロパティが欠落している可能性があることを除いて、タイプチェックに関して `T` と同じプロパティを持ち、ネストされたアルゴリズムやパラメータも再び `RecoPlan` である可能性があります。

プランはネスト可能で、ツリーを形成します。親プランには `parent` でアクセスでき、`parent!` で設定できます。アルゴリズムやパラメータは `toPlan` を使用してプランに変換できます。

プランは `toTOML`、`toPlan`、`loadPlan` を使用したシリアル化機能を備えており、`Òbservables` と `on` を使用してプロパティの変更にコールバックを添付する機能があります。
