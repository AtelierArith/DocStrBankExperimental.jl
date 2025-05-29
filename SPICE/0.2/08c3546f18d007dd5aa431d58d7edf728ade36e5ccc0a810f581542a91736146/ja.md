```
dafrfr(handle, lenout=128)
```

DAFのファイルレコードの内容を読み取ります。

### 引数

  * `handle`: 開いているDAFファイルのハンドル
  * `lenout`: 出力文字列`ifname`の利用可能な領域（デフォルト: 128）

### 出力

  * `nd`: サマリー内の倍精度コンポーネントの数
  * `ni`: サマリー内の整数コンポーネントの数
  * `ifname`: 内部ファイル名
  * `fward`: 前方リストポインタ
  * `bward`: 後方リストポインタ
  * `free`: 自由アドレスポインタ

### 参照

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/dafrfr_c.html)
