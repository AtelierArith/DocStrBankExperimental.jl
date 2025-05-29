```
parsesortcircuit(circuit; sorting = :name)
```

回路を解析してソートします。詳細については、[`parsecircuit`](@ref)、[`sortnodes`](@ref)を参照してください。

# 引数

  * `circuit`: 各コンポーネント名、最初のノード、2番目のノード、およびコンポーネント値を含むタプルのベクター。最初の3つは文字列でなければなりません。

# キーワード

  * `sorting = :name`: 文字列のベクターをソートします。これは常に機能しますが、「101」が「11」の前に来るような結果になります。
  * `sorting = :number`: ノードの文字列を整数に変換し、これに基づいてソートします（ノード名を整数に変換できない場合はエラーになります）。
  * `sorting = :none`: グラウンドノードを最初に配置する以外はソートを行いません。言い換えれば、`circuit`内で見つかった順序でノードを並べます。

# 例

```jldoctest
@variables Ipump Rleft Cc Lj Cj
circuit = Tuple{String,String,String,Num}[]
push!(circuit,("P1","1","0",1))
push!(circuit,("I1","1","0",Ipump))
push!(circuit,("R1","1","0",Rleft))
push!(circuit,("C1","1","2",Cc))
push!(circuit,("Lj1","2","0",Lj))
push!(circuit,("C2","2","0",Cj))
println(parsesortcircuit(circuit))

# 出力
JosephsonCircuits.ParsedSortedCircuit([2 2 2 2 3 3; 1 1 1 3 1 1], ["0", "1", "2"], String[], ["P1", "I1", "R1", "C1", "Lj1", "C2"], [:P, :I, :R, :C, :Lj, :C], Num[1, Ipump, Rleft, Cc, Lj, Cj], Dict("I1" => 2, "C1" => 4, "C2" => 6, "R1" => 3, "P1" => 1, "Lj1" => 5), 3)
```

```jldoctest
@variables Ipump Rleft L1 L2 C2
Kfun(L) = sin(L);@register_symbolic Kfun(L1)
circuit = Tuple{String,String,String,Num}[]
push!(circuit,("P1","1","0",1))
push!(circuit,("I1","1","0",Ipump))
push!(circuit,("R1","1","0",Rleft))
push!(circuit,("L1","1","0",L1)) 
push!(circuit,("K1","L1","L2",Kfun(L1)))
push!(circuit,("L2","2","0",L2)) 
push!(circuit,("C2","2","0",C2))
println(parsesortcircuit(circuit))

# 出力
JosephsonCircuits.ParsedSortedCircuit([2 2 2 2 0 3 3; 1 1 1 1 0 1 1], ["0", "1", "2"], ["L1", "L2"], ["P1", "I1", "R1", "L1", "K1", "L2", "C2"], [:P, :I, :R, :L, :K, :L, :C], Num[1, Ipump, Rleft, L1, Kfun(L1), L2, C2], Dict("L1" => 4, "I1" => 2, "L2" => 6, "C2" => 7, "R1" => 3, "P1" => 1, "K1" => 5), 3)
```
