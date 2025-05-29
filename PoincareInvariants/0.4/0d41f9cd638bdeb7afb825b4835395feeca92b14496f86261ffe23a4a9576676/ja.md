```
compute!(pinv::AbstractPoincareInvariant, points::AbstractMatrix, t::Real=NaN, p=nothing)
```

は、セットアップオブジェクト `pinv` を使用してポアンカレ不変量を計算します。ここで、`points` は曲線または表面のパラメータ化の画像を、いくつかの点のセット（例えば、グリッド）で評価したものを表します。

`t` は不変量が評価される時間であり、`p` はユーザーが提供する任意のオプション引数です。`t` と `p` はどちらも微分形式に直接渡されます。

プラン実装は、内部のポイントストレージ `pinv.points` に作用するメソッド `compute!(pinv, t::Real, p)` を定義する必要があります。
