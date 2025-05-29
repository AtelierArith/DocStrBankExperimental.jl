```
@distinct!(d, args...)
```

`AbstractDataFrame`内のユニークな行をインプレースで選択します。ユーザーは、`@distinct!`がDataFrames.jlの`unique!`とは異なることに注意する必要があります。たとえば、`@distinct!(df, [:x,:y])`は`unique(df, [:x,:y])`とは等しくありません。これらの違いについては**詳細**を参照してください。

### 引数

  * `d` : AbstractDataFrame
  * `args...` :   列を指定するための`:x`の形式の変換またはその変換を指定する`f(:x)`

### 戻り値

  * `::AbstractDataFrame`

`@distinct!`への入力は、`begin ... end`ブロックの形式または一連の引数およびキーワードのような引数の形式で提供できます。たとえば、以下は同等です。

```julia
@distinct! df begin 
    :x .+ :y
end
```

および 

```
@distinct!(df, :x .+ :y)
```

`@distinct!`は、`ByRow`関数ラッパーからの変換をラップするために`@byrow`構文を使用し、ブロードキャスティングに似て行ごとに関数を適用します。`@distinct!`は、選択のブロックの最初に`@byrow`を許可します（すなわち、`@byrow begin... end`）。ブロック内の変換は行ごとに操作されます。たとえば、以下の2つの文は同等です。

```
@distinct! df @byrow begin 
    :x + :y
    :z + :t
end
```

および

```
@distinct! df begin 
    @byrow :x + :y
    @byrow :z + :t
end

```

### 詳細

`@distinct!`の実装は、DataFrames.jlの`unique`関数とは異なります。`args`が存在する場合、`@distinct!`は内部の`select`呼び出しに依存し、`args`で指定された`df`の列を含む中間データフレームを生成します。したがって、`df`のユニークな行はこの中間データフレームによって決定されます。この`select`への焦点により、列名や変換の形式で複数の引数を便利に渡すことができます。

ユーザーは、関数引数をベクターとして渡す際に注意する必要があります。たとえば、`@distinct(df, $[:x,:y])`を使用するべきであり、`@distinct(df, [:x,:y])`を使用すると予期しない動作を引き起こす可能性があります。

### 例

```julia
julia> using DataFramesMeta;

julia> df = DataFrame(x = 1:10, y = 10:-1:1);

julia> @distinct!(df, :x .+ :y)
1×2 DataFrame
 Row │ x      y      
     │ Int64  Int64  
─────┼───────────────
   1 │     1      10   

julia> @distinct! df begin
            :x .+ :y
        end
1×2 DataFrame
 Row │ x      y      
     │ Int64  Int64  
─────┼───────────────
   1 │     1      10   
```
