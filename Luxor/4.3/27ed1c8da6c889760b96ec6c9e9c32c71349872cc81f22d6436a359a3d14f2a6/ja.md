```
hascurrentpoint()
```

現在の点がある場合はtrueを返します。これは、`move()`, `line()`, `curve()`, `arc()`, `rline()`, および `rmove()`などのパス構築関数のいずれかによって定義された現在のパスの最も最近の点です。

現在の点を取得するには、`currentpoint()`を使用します。

`strokepath()`および`strokepath()`の呼び出しの後には、現在の点はありません。
