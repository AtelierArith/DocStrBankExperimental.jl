```
ConditionalCrayon
```

ターミナルへの印刷のための条件付きフォーマットを設定します。各 `ConditionalCrayon` は、引数 `x` が受け入れられない場合に `true` を返す関数 `bad(x)` を指定し、色 `cbad` で印刷し、`x` が受け入れられる場合に `true` を返す関数 `good(x)` を指定し、色 `cgood` で印刷します。どちらも `true` でない場合は、色 `cdefault` になります。`bad` 関数は `good` の前にチェックされるため、両方が `true` を返す場合は `bad` が優先されます。これはチェックされません。

すべての色は Crayons.jl の Crayon タイプとして指定する必要があります。

# コンストラクタ

使用は一般的に次のコンストラクタを通じて行われます：

```
ConditionalCrayon(badfun::Function, goodfun::Function; [goodcolor, badcolor, defaultcolor])
```

色は、良い場合は緑、悪い場合は赤、デフォルトの場合はデフォルト色（`Crayon(reset=true)`）にデフォルト設定されています。

範囲で作業する際の便利さのために、次のコンストラクタも提供されています：

```
ConditionalCrayon(lo, hi; [reverse, goodcolor, badcolor, defaultcolor])
```

これは、値が `lo` より小さい場合は良いとし、`hi` より大きい場合は悪いとします。`reverse=true` の場合は逆になります。

デフォルトのコンストラクタ

```
ConditionalCrayon()
```

も提供されており、常にデフォルト色を返します。

# 使用法

`ConditionalCrayon` は、任意の型の単一引数を受け入れ、その入力に対する `good` および `bad` 関数の出力に応じて `Crayon` を返すファンクタオブジェクトです。入力型が関数に適切であることを確認するのはユーザーの責任です（これらはすべてユーザー指定です）。
