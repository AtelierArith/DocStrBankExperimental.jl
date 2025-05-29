```
DebugIfEntry <: DebugAction
```

特定のフィールドが`check`を通過しない場合、警告、情報、またはエラーを発行します。

この場合、`message`が印刷されます。`@printf`引数識別子が含まれている場合、その識別子は`field`の値で埋められます。この方法で、この場合の値を印刷することもできます。

# フィールド

  * `io`:    `IO`ストリーム
  * `check`: フィールドの値を入力として受け取り、ブール値を返す関数
  * `field`: [`AbstractManoptSolverState`](@ref)内でアクセスできるシンボル
  * `msg`:   `check`が失敗した場合に表示されるメッセージ
  * `type`: 表示のタイプを指定するシンボル、可能な値は`:print`、`:warn`、`:info`、`:error`で、`:print`は`io`に印刷します。

# コンストラクタ

```
DebugEntry(field, check=(>(0)); type=:warn, message=":$f is nonnegative", io=stdout)
```
