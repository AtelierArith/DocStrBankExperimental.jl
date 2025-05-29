```
@parametric func iterable
```

`iterable`内の各値に対して、このマクロが呼び出されるモジュールで`TEST_PREFIX`で接頭辞が付けられた`func`のバージョンを作成します。`iterable`内の値がタプルである場合、それは関数の引数にスプラットされます。
