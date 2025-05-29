```
SkipConnection(layers, connection; name=nothing)
SkipConnection(; layers, connection, name=nothing)
```

レイヤーまたは[`Chain`](@ref)の連続レイヤーで構成されるスキップ接続を作成し、ユーザーが提供した2引数のコール可能を介してブロックの入力を出力にリンクするショートカット接続を作成します。コール可能への最初の引数は、指定された`layer`を通じて伝播され、2番目は変更されていない「スキップされた」入力です。

最も単純な「ResNet」タイプの接続は、単に`SkipConnection(layer, +)`です。

## 引数

  * `layer`: 入力に適用されるレイヤーまたはレイヤーの`Chain`
  * `connection`:

      * `layer(input)`と入力を受け取る2引数関数 OR
      * `(layer(input), input)`を入力として受け取るAbstractLuxLayer

# 拡張ヘルプ

## 入力

  * `x`: `layer`に直接渡されます

## 戻り値

  * `connection(layer(input), input)`の出力
  * `layer`の更新された状態

## パラメータ

  * `layer`のパラメータ OR
  * `connection`がAbstractLuxLayerの場合、フィールド`:layers`と`:connection`を持つNamedTuple

## 状態

  * `layer`の状態 OR
  * `connection`がAbstractLuxLayerの場合、フィールド`:layers`と`:connection`を持つNamedTuple

より一般的な実装については[`Parallel`](@ref)を参照してください。
