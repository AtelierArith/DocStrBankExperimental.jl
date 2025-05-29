```
S = Signal(val; strict_push = false)
```

初期値 `val` を持つソース `Signal` を作成します。`strict_push` を `true` に設定すると、この `Signal` へのすべてのプッシュが独立して行われることが保証されます。そうでない場合、`eventloop` が処理できるよりも速く更新が発生した場合、`eventloop` が開始する前の最後の値のみが使用されます（*デフォルト*）。

```
S = Signal(f,args...; v0 = nothing)
```

値が `f(args...)` である派生 `Signal` を作成します。`args` は任意の型であり、`Signal` の引数は `f(args...)` を呼び出す前にその値に置き換えられます。`do` 構文での使用が最適です（例を参照）。`v0` が `nothing` でない場合、`Signal` の作成後に `f(args...)` は直接呼び出されず、`Signal` は値 `v0` を持つように初期化されます。

# 構文

```
S[] = val
```

`S` の値を `val` に設定しますが、信号グラフの残りの部分に変更を伝播させません。プルベースのパラダイムで便利です。

```
S()
```

`pull!` Signal。`S` に影響を与える信号グラフの変更をプルします。

```
S(val)
```

`S` の値を `val` に設定し、信号グラフに沿って変更をプッシュします。

```
S[]
```

グラフから変更をプルせずに、`S` に格納されている現在の値を取得します。

# 例

```
julia> A = Signal(1) # ソース Signal
Signal
value: 1

julia> B = 2 # 非 Signal 入力
2

julia> C = Signal(A, B) do a, b # 派生 Signal
           a + b
       end

Signal
value: 3

julia> A[] = 10 # 伝播なしで値を設定
10
julia> C[] # 現在の値を読み取る
3
julia> C() # 信号グラフから最新の変更をプル
12
julia> A(100) # 信号に値を設定し、この変更を伝播
100
julia> C[]
102
```
