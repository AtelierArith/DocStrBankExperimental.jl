```
entr(f, files; all=false, postpone=false, pause=0.02)
entr(f, files, modules; all=false, postpone=false, pause=0.02)
```

`files` にリストされたファイルやディレクトリ、または `modules` のコードが更新されるたびに `f()` を実行します。`all` が `true` の場合、Revise によって追跡されている任意のモジュールでコードの更新が検出されると、すぐに `f()` も実行されます。

`entr` は更新を処理し（コマンドラインをブロックし）、Ctrl-C を押すまで続きます。`postpone` が `true` でない限り、ファイルの変更に関係なく `entr` を呼び出すときにも `f()` が実行されます。`pause` は、`entr` がトリガーされてから実際に `f()` を呼び出すまでの待機時間（秒単位）で、特定のテキストエディタでファイルを保存することによって生成される変更のクラスターを処理するために使用されます。

# 例

```julia
entr(["/tmp/watched.txt"], [Pkg1, Pkg2]) do
    println("update")
end
```

これにより、`"/tmp/watched.txt"` または `Pkg1` または `Pkg2` を定義するコードが更新されるたびに "update" が印刷されます。
