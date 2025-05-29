```
writehrse(io::IO, obj, options::HrsePrintOptions)
writehrse(obj, options::HrsePrintOptions)
```

指定されたJuliaオブジェクトを指定されたIOオブジェクトにHRSEファイルとして書き込みます。`options`引数はプリンタの動作を構成するために使用できます。IOオブジェクトが指定されていない場合、出力は`stdout`に書き込まれます。任意のオブジェクトはそのStructTypes.StructTypeを使用してシリアライズされます。

# 例

```jldoctest
julia> using HumanReadableSExpressions

julia> hrse = [
           :alpha => [
               [1, 2, 3, 4],
               [5, 6],
               [7, 8, 9]
           ],
           :beta => (0 => 3),
           :gamma => [
               :a => 1
               :b => 2
               :c => :c
           ]
       ];

julia> writehrse(hrse, HumanReadableSExpressions.HrsePrintOptions())
alpha: 
  1 2 3 4
  5 6
  7 8 9
beta: 0: 3
gamma: 
  a: 1
  b: 2
  c: c
```

さらに[`HrsePrintOptions`](@ref)を参照してください。
