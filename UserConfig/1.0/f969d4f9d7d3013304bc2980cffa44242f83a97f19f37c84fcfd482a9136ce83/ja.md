```
strout = localstring(title, checkfun=s->true)
```

ユーザー特有の文字列を取得し、ユーザーが以前にそれを提供していないか尋ねます。 checkfun(string) が実行され、true の場合のみ文字列を返します。
