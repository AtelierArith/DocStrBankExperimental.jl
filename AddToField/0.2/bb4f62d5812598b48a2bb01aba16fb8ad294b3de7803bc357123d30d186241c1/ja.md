```
@addnt(body)
```

`body`内で`@add`ステートメントを使用して名前付きタプルを作成します。

### 使用法

`body`内では、以下の構文を使用して名前付きタプルを作成できます。

  * `@add x`: 名前付きタプルには、値が`x`のフィールド`:x`が含まれます。
  * `@add x, y, z`: 名前付きタプルには、対応する値を持つフィールド`x`、`y`、`z`が含まれます。
  * `@add x = expr`: 名前付きタプルには、値が`expr`のフィールド`:x`が含まれます。変数`x`はまだ作成されます。
  * `@add "My value" x`: 名前付きタプルには、値が`x`のフィールド`Symbol("My value")`が含まれます。`String`名の中に値を補間することもできます。
  * `@add "My value" x = expr`: 名前付きタプルには、値が`expr`のフィールド`Symbol("My value")`が含まれます。変数`x`はまだ作成されます。

`@addnt begin ... end`は新しいスコープを作成しないため、式内のすべての変数の割り当ての変更は既存のスコープを修正します。新しいスコープを作成するには、`@addnt let ... end`を使用します。

### 例:

```jldoctest
julia> s = "My long name";

julia> res = @addnt begin
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
(a = 1, f = 6, g = 7, h = 8, b = 2, c1 = 3, d1 = 4, My long name = 5)

julia> @addnt let
           @add local_var = 500
       end
(local_var = 500,)

julia> isdefined(Main, :local_var)
false
```

!!! note
    `You`は`body`で作成された新しいスコープ内で`@add`を使用することはできません。以下は失敗します。

    ```julia
    @addnt begin
    	let
    	    a = 1
    	    @add a
    	end
    end
    ```

    これは、`@addnt`が匿名変数を作成し、その後式の最後で名前付きタプルを構築するためです。同様のことが`@addnt`および`@addto!`ブロック内の`for`ループや`function`にも当てはまります。

