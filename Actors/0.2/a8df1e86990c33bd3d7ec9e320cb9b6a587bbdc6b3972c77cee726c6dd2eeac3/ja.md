```
Link{C} <: ActorInterfaces.Classic.Addr
Link(chn::C, pid::Int, type::Symbol) where C
```

アクターとの通信のためのメールボックス。これの具体的な型は、アクターが[`spawn`](@ref)で作成される際に返されなければなりません。

# フィールド/パラメータ

  * `chn::C`: Cは任意の型であり、アクターへのインターフェースを特徴付けます。
  * `pid::Int`: アクターのpid（ワーカープロセス識別子）。
  * `mode::Symbol`: アクターのモードを特徴付けるシンボル。
