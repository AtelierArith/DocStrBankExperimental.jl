```
compile(code; name="score", argv=[], target="", opt=-1)
```

`code`を`DSPBlock`にコンパイルします。

# 引数

  * `argv::Vector{String}`: Faustコンパイラへの引数のリスト。例: "-double": 倍精度   "-vec": コードをベクトル化します。
  * `target::String`: LLVM IRをビルドする対象。デフォルトは現在のマシンです。
  * `opt::Integer`: -1は「利用可能な最高レベル」です。

# 例

```julia-repl
julia> d = compile("import("stdfaust.lib"); process = os.osc(freq) : *(0.25) <: _, _;")
```
