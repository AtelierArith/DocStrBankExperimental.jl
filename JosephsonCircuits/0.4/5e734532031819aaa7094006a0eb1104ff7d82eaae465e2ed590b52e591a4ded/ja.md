```
parsecircuit(circuit)
```

`circuit`を解析します。`circuit`は、各要素がコンポーネント名、最初のノード、2番目のノード、およびコンポーネント値を含むタプルのベクターです。コンポーネント値は数値、シンボル、またはシンボリック変数（シンボリック関数を含む）であることができます。

ノードはSPICE互換性のために任意の文字列を使用できます。整数もサポートされていますが、内部的には文字列に変換されます。グラウンドノードは「0」であり、必須です。ベクター`circuit`の型を指定することはオプションですが、通常は型ユニオンを持つベクターが、型Anyの配列よりも好まれます。

# 引数

  * `circuit`: 各タプルがコンポーネント名、最初のノード、2番目のノード、およびコンポーネント値を含むタプルのベクター。

# 例

```jldoctest
@variables Ipump Rleft L1 K1 L2 C2
circuit = Vector{Tuple{String,String,String,Num}}(undef,0)
push!(circuit,("P1","1","0",1))
push!(circuit,("I1","1","0",Ipump))
push!(circuit,("R1","1","0",Rleft))
push!(circuit,("L1","1","0",L1))
push!(circuit,("K1","L1","L2",K1))
push!(circuit,("L2","2","0",L2))
push!(circuit,("C2","2","0",C2))
parsecircuit(circuit)

# 出力
JosephsonCircuits.ParsedCircuit([1, 2, 1, 2, 1, 2, 1, 2, 0, 0, 3, 2, 3, 2], ["1", "0", "2"], ["L1", "L2"], ["P1", "I1", "R1", "L1", "K1", "L2", "C2"], [:P, :I, :R, :L, :K, :L, :C], Num[1, Ipump, Rleft, L1, K1, L2, C2], Dict("L1" => 4, "I1" => 2, "L2" => 6, "C2" => 7, "R1" => 3, "P1" => 1, "K1" => 5), 3)
```

```jldoctest
@variables Ipump Rleft L1 L2 C2
Kfun(L) = sin(L);@register_symbolic Kfun(L1)
circuit = Vector{Tuple{String,String,String,Num}}(undef,0)
push!(circuit,("P1","1","0",1))
push!(circuit,("I1","1","0",Ipump))
push!(circuit,("R1","1","0",Rleft))
push!(circuit,("L1","1","0",L1))
push!(circuit,("K1","L1","L2",Kfun(L1)))
push!(circuit,("L2","2","0",L2))
push!(circuit,("C2","2","0",C2))
parsecircuit(circuit)

# 出力
JosephsonCircuits.ParsedCircuit([1, 2, 1, 2, 1, 2, 1, 2, 0, 0, 3, 2, 3, 2], ["1", "0", "2"], ["L1", "L2"], ["P1", "I1", "R1", "L1", "K1", "L2", "C2"], [:P, :I, :R, :L, :K, :L, :C], Num[1, Ipump, Rleft, L1, Kfun(L1), L2, C2], Dict("L1" => 4, "I1" => 2, "L2" => 6, "C2" => 7, "R1" => 3, "P1" => 1, "K1" => 5), 3)
```

```jldoctest
circuit = Vector{Tuple{String,String,String,Union{Complex{Float64}, Symbol,Int}}}(undef,0)
push!(circuit,("P1","1","0",1))
push!(circuit,("I1","1","0",:Ipump))
push!(circuit,("R1","1","0",:Rleft))
push!(circuit,("C1","1","2",:Cc))
push!(circuit,("Lj1","2","0",:Lj))
push!(circuit,("C2","2","0",:Cj))
parsecircuit(circuit)

# 出力
JosephsonCircuits.ParsedCircuit([1, 2, 1, 2, 1, 2, 1, 3, 3, 2, 3, 2], ["1", "0", "2"], String[], ["P1", "I1", "R1", "C1", "Lj1", "C2"], [:P, :I, :R, :C, :Lj, :C], Union{Int64, Symbol, ComplexF64}[1, :Ipump, :Rleft, :Cc, :Lj, :Cj], Dict("I1" => 2, "C1" => 4, "C2" => 6, "R1" => 3, "P1" => 1, "Lj1" => 5), 3)
```

```jldoctest
circuit = Vector{Tuple{String,String,String,Union{Complex{Float64}, Symbol,Int}}}(undef,0)
push!(circuit,("P1","One","0",1))
push!(circuit,("I1","One","0",:Ipump))
push!(circuit,("R1","One","0",:Rleft))
push!(circuit,("C1","One","Two",:Cc))
push!(circuit,("Lj1","Two","0",:Lj))
push!(circuit,("C2","Two","0",:Cj))
parsecircuit(circuit)

# 出力
JosephsonCircuits.ParsedCircuit([1, 2, 1, 2, 1, 2, 1, 3, 3, 2, 3, 2], ["One", "0", "Two"], String[], ["P1", "I1", "R1", "C1", "Lj1", "C2"], [:P, :I, :R, :C, :Lj, :C], Union{Int64, Symbol, ComplexF64}[1, :Ipump, :Rleft, :Cc, :Lj, :Cj], Dict("I1" => 2, "C1" => 4, "C2" => 6, "R1" => 3, "P1" => 1, "Lj1" => 5), 3)
```

```jldoctest
circuit = []
push!(circuit,("P1","1","0",1))
push!(circuit,("I1","1","0",:Ipump))
push!(circuit,("R1","1","0",:Rleft))
push!(circuit,("C1","1","2",:Cc))
push!(circuit,("Lj1","2","0",:Lj))
push!(circuit,("C2","2","0",:Cj))
parsecircuit(circuit)

# 出力
JosephsonCircuits.ParsedCircuit([1, 2, 1, 2, 1, 2, 1, 3, 3, 2, 3, 2], ["1", "0", "2"], String[], ["P1", "I1", "R1", "C1", "Lj1", "C2"], [:P, :I, :R, :C, :Lj, :C], Any[1, :Ipump, :Rleft, :Cc, :Lj, :Cj], Dict("I1" => 2, "C1" => 4, "C2" => 6, "R1" => 3, "P1" => 1, "Lj1" => 5), 3)
```

```jldoctest
circuit = Vector{Tuple{String,String,String,Union{Complex{Float64}, Symbol,Int}}}(undef,0)
push!(circuit,("P1","1","0",1))
push!(circuit,("I1","1","0",:Ipump))
push!(circuit,("R1","1","0",:Rleft))
push!(circuit,("L1","1","0",:L1))
push!(circuit,("K1","L1","L2",:K1))
push!(circuit,("L2","2","0",:L2))
push!(circuit,("C2","2","0",:C2))
parsecircuit(circuit)

# 出力
JosephsonCircuits.ParsedCircuit([1, 2, 1, 2, 1, 2, 1, 2, 0, 0, 3, 2, 3, 2], ["1", "0", "2"], ["L1", "L2"], ["P1", "I1", "R1", "L1", "K1", "L2", "C2"], [:P, :I, :R, :L, :K, :L, :C], Union{Int64, Symbol, ComplexF64}[1, :Ipump, :Rleft, :L1, :K1, :L2, :C2], Dict("L1" => 4, "I1" => 2, "L2" => 6, "C2" => 7, "R1" => 3, "P1" => 1, "K1" => 5), 3)
```
