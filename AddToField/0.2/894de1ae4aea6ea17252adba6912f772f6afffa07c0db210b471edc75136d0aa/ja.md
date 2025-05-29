```
@adddict(body)
```

`body`内で`@add`文を使用して、`Symbol`をキーとする`Dict`を作成します。

### 使用法

`body`内では、以下の構文を使用して`Dict`を作成できます。

  * `@add x`: `Dict`には、`x`の値を持つフィールド`:x`が含まれます。
  * `@add x, y, z`: `Dict`には、対応する値を持つフィールド`x`、`y`、`z`が含まれます。
  * `@add x = expr`: `Dict`には、`expr`の値を持つフィールド`:x`が含まれます。変数`x`はまだ作成されます。
  * `@add "My value" x`: `Dict`には、`x`の値を持つフィールド`Symbol("My value")`が含まれます。`String`名の中に値を補間することもできます。
  * `@add "My value" x = expr`: `Dict`には、`expr`の値を持つフィールド`Symbol("My value")`が含まれます。変数`x`はまだ作成されます。

`@addict begin ... end`は新しいスコープを作成しないため、式内のすべての変数の割り当ての変更は既存のスコープを修正します。新しいスコープを作成するには、`@adddict let ... end`を使用します。

### 例:

```jldoctest
julia> s = "My long name";

julia> res = @adddict begin
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
Dict{Symbol, Int64} with 8 entries:
  :a                     => 1
  :f                     => 6
  :b                     => 2
  :h                     => 8
  :g                     => 7
  :d1                    => 4
  :c1                    => 3
  Symbol("My long name") => 5

julia> @adddict let
           @add local_var = 500
       end
Dict{Symbol, Int64} with 1 entry:
  :local_var => 500

julia> isdefined(Main, :local_var)
false
```

!!! note
    `body`で作成された新しいスコープ内では`@add`を使用できません。以下は失敗します。

    ```julia
    @adddict begin
    	let
    	    a = 1
    	    @add a
    	end
    end
    ```

    これは、`@adddict`が匿名変数を作成し、式の最後で`Dict`を構築するためです。同様のことが`@addict`ブロック内の`for`ループや`function`にも当てはまります。

