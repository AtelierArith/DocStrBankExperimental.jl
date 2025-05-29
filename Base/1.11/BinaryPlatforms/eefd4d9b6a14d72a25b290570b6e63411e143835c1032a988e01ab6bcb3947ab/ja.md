```
プラットフォーム
```

`Platform` は、プロセッサアーキテクチャ、オペレーティングシステム、libc 実装など、julia プロセスが実行環境について知っておく必要のあるすべての関連情報を表します。 本質的には、タグ（`arch`、`os`、`libc` など）と値（`"arch" => "x86_64"` や `"os" => "windows"` など）のキーと値のマッピングです。 `Platform` オブジェクトは拡張可能であり、ユーザーが予約されたタグのセット（`arch`、`os`、`os_version`、`libc`、`call_abi`、`libgfortran_version`、`libstdcxx_version`、`cxxstring_abi`、`julia_version`）と競合しない限り、自分のマッピングを追加することができます。

有効なタグと値は、英数字とピリオドの文字で構成されます。 すべてのタグと値は、変動を減らすために保存時に小文字に変換されます。

例:

```
Platform("x86_64", "windows"; cuda = "10.1")
```
