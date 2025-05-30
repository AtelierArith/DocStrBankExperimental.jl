```
sp_flush(port::Port, buffers::SPBuffer)
sp_flush(port::SerialPort, buffers::SPBuffer)
```

選択したシリアルポートバッファのデータを破棄します。

`buffers` にサポートされている値: `SP_BUF_INPUT`, `SP_BUF_OUTPUT`, `SP_BUF_BOTH`

成功した場合は `SP_OK` を返し、そうでない場合は `ErrorException` を発生させます。

!!! note
    バッファされたデータを書き出す `Base.flush` と混同しないでください: 基本的な `libserialport` C ライブラリは、残念ながら `Base.IO` の通常の意味とは異なる「フラッシュ」という動詞を使用しています（このライブラリでは `sp_drain` が後者を提供します）。

