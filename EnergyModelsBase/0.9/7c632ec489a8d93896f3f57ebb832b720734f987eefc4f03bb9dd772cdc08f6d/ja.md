```
StorageInvData <: InvestmentData
```

ストレージ投資のための追加投資データ。ストレージ投資のための追加投資データは、ストレージの充電容量（**`charge`**）、ストレージ容量の増加（**`level`**）、またはストレージの放電容量（**`discharge`**）の投資データを含むことができますが、必ずしも必要ではありません。

個々のパラメータのためにキーワード引数を持つコンストラクタを利用します。したがって、パラメータの名前を指定する必要があります。

# フィールド

  * **`charge::Union{AbstractInvData, Nothing}`** は充電容量のための投資データです。
  * **`level::Union{AbstractInvData, Nothing}`** はレベル容量のための投資データです。
  * **`discharge::Union{AbstractInvData, Nothing}`** は放電容量のための投資データです。
