```
AbstractInput
```

すべての入力タイプのための抽象スーパタイプ。

### ノート

ここで定義された入力タイプは、イテレータインターフェースを実装しており、他のメソッドが定数または変動する入力の動作に基づいて構築できるようになっています。

イテレーションは、*イテレータ状態*と呼ばれるインデックス番号でサポートされています。イテレーション関数 `Base.iterate` はタプル（`input`、`state`）を受け取り、返します。ここで `input` は入力の値を表し、`state` はこのイテレータが呼び出された回数をカウントするインデックスです。

便利な関数 `nextinput(input, n)` も提供されており、`input` の最初の `n` 要素を返します。
