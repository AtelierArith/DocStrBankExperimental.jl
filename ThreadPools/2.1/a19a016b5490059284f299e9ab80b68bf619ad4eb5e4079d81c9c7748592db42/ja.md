```
spawnbg(f)
```

任意の利用可能なバックグラウンドスレッドで作業を開始します。スレッド内でスローされた例外をキャプチャし、より良いスタックトレースを提供します。

`checked_fetch(spawnbg(f))`を使用して、例外を再スローすることができます。

```
** 警告 ** これは他のスレッドのスケジューリング方法と組み合わせることはできません
したがって、各Juliaプロセスで`spawn_background`を排他的に使用する必要があります。
```
