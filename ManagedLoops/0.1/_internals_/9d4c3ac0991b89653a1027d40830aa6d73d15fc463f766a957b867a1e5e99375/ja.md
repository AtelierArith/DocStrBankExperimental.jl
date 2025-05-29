## 一引数形式

```
@unroll expr
```

次の構造を `expr` 内で展開します：

```
for i in start:stop ... end
(expr for i in start:stop)
sum(expr for i=start:stop ... end)
```

整数 `start` と `stop` が *パース* 時に既知である場合に限ります。展開は `expr` に含まれるサブ式に再帰的に適用されます。

!!! 例

```
    @unroll for i=4:6 ; foo(i); end
    @unroll (i*i for i=4:6)
    @unroll sum(i * i for i=4:6)
    ```

    は次のように展開されます

    ```
    begin; foo(4); foo(5); foo(6) ; end
    (4*4, 5*5, 6*6)
    4*4 + 5*5 + 6*6
    ```


## 二引数形式

```

@unroll n in start:stop expr(n)

```

次のように展開されます

```

if n==start ; @unroll expr(start) ; end if n==start+1 ; @unroll expr(start+1) ; end ... if n==stop ; @unroll expr(stop) ; end ```

整数 `start` と `stop` がパース時に既知である場合に限ります。展開は `expr` とそのサブ式に再帰的に適用されます。

!!! 警告     @unroll のネストされた使用は決して必要ではなく、サポートされておらず、期待通りに動作しない可能性があります。
