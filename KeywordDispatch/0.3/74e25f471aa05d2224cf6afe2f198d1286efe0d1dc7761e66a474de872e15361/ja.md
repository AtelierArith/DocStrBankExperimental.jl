```
@kwdispatch sig [methods]
```

キーワード引数に基づいてディスパッチする関数シグネチャ `sig` を指定します。関数を提供することもでき、その場合はその関数へのすべての呼び出しがキーワードメソッドにディスパッチされます。

キーワードの位置に `from => to` ペアを指定することで、キーワードエイリアスを指定することが可能です。

オプションの `methods` 引数は、匿名関数として指定されたキーワードメソッドのブロックを許可します。追加のキーワードメソッドを定義するには、[`@kwmethod`](@ref) マクロを使用します。

# 例

```julia
@kwdispatch f(_)
@kwdispatch f(_::Real)

@kwdispacth f # @kwdispatch f(_...) と同等

@kwdispatch f(x) begin
    (a) -> x+a
    (b) -> x-b
end
# 同等のもの
#  @kwdispatch f(x)
#  @kwmethod f(x;a) = x+a
#  @kwmethod f(x;b) = x-b

@kwdispatch f(; alpha=>α) # α のエイリアスとして alpha を指定
```
