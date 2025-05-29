```
DataLoader(
    data,
    batchsize = 1;
    partial = true,
    collate = true,
    buffered = collate,
    parallel = Threads.nthreads() > 1,
    useprimary = false,
)
```

[データコンテナ](../documents/docs/datacontainers.md) `data` のバッチの効率的なイテレータを作成します。

## 引数

位置引数

  * `data`: `LearnBase` データアクセスパターンをサポートするデータコンテナ
  * `batchsize = 1`: 一緒にバッチするサンプルの数。`nothing` に設定することでバッチ処理を無効にします。

キーワード引数

  * `partial::Bool = true`: `nobs(dataset)` が `batchsize` で割り切れない場合に最後のバッチを含めるかどうか。`true` にするとすべてのバッチが同じサイズになりますが、一部のサンプルがドロップされる可能性があります。
  * `buffered::Bool = collate`: `buffered` が `true` の場合、`getobs!` を使用してデータをインプレースでロードします。バッファロードの詳細については [データコンテナ](../documents/docs/datacontainers.md) を参照してください。
  * `parallel::Bool = Threads.nthreads() > 1)`: データを並列にロードするかどうか、プライマリスレッドを保持します。スレッドが1つ以上利用可能な場合はデフォルトで `true` です。
  * `useprimary::Bool = false`: `false` の場合、データを並列にロードする際にメインスレッドを空けておきます。`parallel` が `false` の場合は無視されます。

## 例

バッチサイズ16のデータローダーを作成し、それを反復処理する：

```julia
data = (rand(128, 10000), rand(1, 10000))
dataloader = DataLoader(data, 16)

for (xs, ys) in dataloader
end
```

バッチをロードするために [バッファ](../documents/docs/inplaceloading.md) を使用するデータローダーを作成する：

```julia
data = rand(100, 64)
dataloader = DataLoader(data, 16, buffered=true)

size(first(dataloader)) == (100, 16)
```

[コレート](../documents/docs/collate.md) をオフにする：

```julia
dataloader = DataLoader(data, 16, collate=false)

# バッチは観測のベクトルです
length(first(dataloader)) == 16
```
