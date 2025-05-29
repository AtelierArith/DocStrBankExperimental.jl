```
dafgsr(handle, recno, start, stop)
```

DAFファイルのサマリーレコードの内容の一部を読み取ります。

### 引数

  * `handle`: DAFのハンドル
  * `recno`: レコード番号
  * `start`: レコードから読み取る最初の単語
  * `stop`: レコードから読み取る最後の単語

### 出力

レコードの内容を返すか、見つからなかった場合は`nothing`を返します。

### 参照

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/dafgsr_c.html)
