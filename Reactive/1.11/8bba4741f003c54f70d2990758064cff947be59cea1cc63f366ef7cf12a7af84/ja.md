```
preserve(signal::Signal)
```

は、`signal` の親が存在する限り、`signal` がガーベジコレクトされるのを防ぎます。これは、信号で副作用を行いたいときに便利です。例えば、`preserve(map(println, x))` - これは、x がスコープを外れるまで、x の更新を印刷し続けます。`foreach` は、`preserve` を使った `map` のショートハンドです。
