```
@f_str(string::AbstractString)

Pythonスタイルの`fstring`リテラル文字列補間の緩やかな実装で、`Printf.@sprintf`に基づいています。
```

# 例

```julia-repl
julia> using FStrings
julia> f"π ≈ {π:.2f}"
"π ≈ 3.14"
```

# フォーマット指定子

利用可能なフォーマット指定子の詳細については、`Printf.@sprintf`を参照してください。また、PEP 498を通じて`fstring`の基本構文も参照してください。

# 参考文献

  * [`Printf.@sprintf`]: https://docs.julialang.org/en/v1/stdlib/Printf/#Printf.@sprintf
  * [PEP 498]: https://www.python.org/dev/peps/pep-0498/
