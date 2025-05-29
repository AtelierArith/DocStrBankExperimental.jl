# コンストラクタ

```
LazyPartition{PType}()
```

タイプ `PType` のパーティションをラップするための空の `LazyPartition` を初期化します。

# 説明

このデータ構造を使用すると、選択したパーティションをラップできます。アイデアは、いくつかのメッセージパッシングアルゴリズムでは、実際に実行する必要があるパーティションの波だけが存在するということです。たとえば、ルートから葉へのパスに沿った波や、深さ優先探索の場合です。この場合、メモリ消費をより経済的にすることができます。最悪の場合のメモリ複雑度は O(log(n)) であり、ここで n はノードの数です。以下の機能が提供されます：

  * `log_likelihood!`
  * `felsenstein!`
  * `sample_down!`

!!! 注     連続した `felsenstein!` 呼び出しのために、各呼び出しの後にルートで情報を抽出する必要があります。これは、例えば `total_LL` や `site_LLs` を使用して行うことができます。

# さらなる要件

`LazyPartition` で `PType` のパーティションをラップしたいとします：

  * `log_likelihood!` と `felsenstein!` を呼び出す場合：

      * 観測をパーティションに変換する `obs2partition!(partition::PType, obs)`。
  * `sample_down!` を呼び出す場合：

      * パーティションから最も可能性の高い状態を返す `partition2obs(partition::PType)`、これは `obs2partition!` を逆転させます。
