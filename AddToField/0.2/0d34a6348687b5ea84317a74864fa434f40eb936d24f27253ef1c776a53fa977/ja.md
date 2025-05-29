```
@addto!(x, body)
```

`body`内で`@add`文を使用して`x`のプロパティまたはインデックスを設定します。

### 使用法

`body`内では、次の方法で`x`のプロパティまたはインデックスを追加できます。

  * `@add x`: 名前付きタプルは、`x`の値を持つフィールド`:x`を含みます。
  * `@add x, y, z`: 名前付きタプルは、対応する値を持つフィールド`x`、`y`、`z`を含みます。
  * `@add x = expr`: 名前付きタプルは、`expr`の値を持つフィールド`:x`を含みます。変数`x`はまだ作成されます。
  * `@add "My value" x`: 名前付きタプルは、`x`の値を持つフィールド`Symbol("My value")`を含みます。`String`名の中に値を補間することもできます。
  * `@add "My value" x = expr`: 名前付きタプルは、`expr`の値を持つフィールド`Symbol("My value")`を含みます。変数`x`はまだ作成されます。

`@addto!`はデフォルトで`x`に対して`setproperty!`を呼び出します。しかし、`AbstractDict`の場合、`Symbol`を使って`setindex!`を呼び出します。`AbstractDict{<:AbstractString}`の場合は、`String`を使って`setindex!`を呼び出します。

`@addto! d begin ... end`は新しいスコープを作成しないため、式内のすべての変数の割り当ての変更は既存のスコープを修正します。新しいスコープを作成するには、`@addto! d let ... end`を使用します。

### 例:

```jldoctest
julia> D = Dict();

julia> s = "My long name";

julia> res = @addto! D begin
		a = 1
		@add a

		f, g, h = 6, 7, 8
		@add f, g, h

		@add b = 2
		@add :c1 c = 3
		@add "d1" d = 4
		@add "My long name" e = 5
	end
end
Dict{Any,Any} with 8 entries:
  :a                     => 1
  :f                     => 6
  :b                     => 2
  :h                     => 8
  :g                     => 7
  :d1                    => 4
  :c1                    => 3
  Symbol("My long name") => 5

julia> @addto! d let
           @add local_var = 500
       end;

julia> isdefined(Main, :local_var)
false
```

!!! note
    `body`で作成された新しいスコープ内で`@addto!`を使用することはできません。次のコードは失敗します。

    ```julia
    @addto! D begin
    	let
    	    a = 1
    	    @add a
    	end
    end
    ```

    これは、`@addto!`が匿名変数を作成し、式の最後で`setproperty!`または`setindex!`の呼び出しを構築するためです。


```
