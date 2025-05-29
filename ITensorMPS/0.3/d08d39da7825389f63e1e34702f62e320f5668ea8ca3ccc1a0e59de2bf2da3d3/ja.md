```
add!(opsum::OpSum,
     op1::String, i1::Int)

add!(opsum::OpSum,
     coef::Number,
     op1::String, i1::Int)

add!(opsum::OpSum,
     op1::String, i1::Int,
     op2::String, i2::Int,
     ops...)

add!(opsum::OpSum,
     coef::Number,
     op1::String, i1::Int,
     op2::String, i2::Int,
     ops...)

+(opsum:OpSum, term::Tuple)
```

OpSum `opsum` に単一または複数サイトの演算子項を追加します。各演算子は名前（String）とサイト番号（Int）によって指定されます。2番目のバージョンは実数または複素数の係数を受け入れます。

この関数の `+` 演算子バージョンは、(String,Int,String,Int,...) または (Number,String,Int,String,Int,...) のいずれかのエントリを持つタプルを受け入れます。これらのタプルの値は、`add!` 関数への有効な入力と同じです。OpSum に非常に多くの項（タプル）を入力する場合は、各追加後に OpSum を再割り当てすることを避けるために、ブロードキャスト演算子 `.+=` の使用を検討してください。

# 例

```julia
opsum = OpSum()

add!(opsum,"Sz",2,"Sz",3)

opsum += ("Sz",3,"Sz",4)

opsum += (0.5,"S+",4,"S-",5)

opsum .+= (0.5,"S+",5,"S-",6)
```
