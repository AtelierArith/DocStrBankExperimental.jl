```julia
structural_simplify(sys; ...)
structural_simplify(
    sys,
    io;
    additional_passes,
    simplify,
    split,
    allow_symbolic,
    allow_parameter,
    conservative,
    fully_determined,
    kwargs...
)

```

システム内の代数方程式を構造的に簡素化し、`sys`内の観測方程式のトポロジカルソートを計算します。

### オプション引数:

  * オプション引数 `io` はタプル `(inputs, outputs)` を取ることができます。これにより、すべての `inputs` がパラメータに変換され、接続されていないことが許可されます。すなわち、簡素化は `n_unknowns = n_equations - n_inputs` のモデルを許可します。

### オプションキーワード引数:

  * `simplify=true` の場合、`simplify` 関数がティアリングプロセス中に適用されます。
  * `allow_symbolic=false`、`allow_parameter=true`、および `conservative=false` は、ティアリング中の係数の種類を制限します。特に、`conservative=true` は、係数の絶対値が $1$ である自明な線形システムのみを解くようにティアリングを制限します。
  * `fully_determined=true` は、方程式の数が入力、出力、および方程式の数と一致しない場合にエラーがスローされるかどうかを制御します。
  * `sort_eqs=true` は、簡素化の前に方程式が辞書順にソートされるかどうかを制御します。
