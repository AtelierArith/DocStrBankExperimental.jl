```
@no_escape([buf=default_buffer()], expr)
```

現在の`buf`の状態を記録します（引数が1つだけの場合は`default_buffer()`がデフォルトになります）。その後、`expr`内のコードを実行し、コードが実行される前の状態に`buf`をリセットします。これにより、`@alloc`を使用して`expr`内でメモリを割り当て、その後、式が終了すると自動的に配列が解放されるようになります。これは制限的ですが非常に効率的なメモリ管理の形式です。

`Bumper.checkpoint_save`および`Bumper.checkpoint_restore!`も参照してください。

`@no_escape`ブロック内で`return`、`@goto`、および`@label`を使用することはできません。

例:

```
function f(x::Vector{Int})
    # メモリが割り当てられるスコープを設定し、エスケープしない:
    @no_escape begin
        # デフォルトバッファからメモリを使用してUnsafeArrays.jlから`UnsafeArray`を割り当てる。
        y = @alloc(Int, length(x))
        # そのベクトルでいくつかの処理を行う:
        y .= x .+ 1
       sum(y)
    end
end
```
