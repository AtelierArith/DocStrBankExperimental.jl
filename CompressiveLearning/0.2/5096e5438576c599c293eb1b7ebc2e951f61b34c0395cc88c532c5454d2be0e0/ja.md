```julia
CLOMPR(
    s,
    k,
    prmType,
    A;
    replacement,
    weights_update_method,
    weights_update,
    bound_alpha,
    init_method,
    init_bounds,
    init_extra_params,
    maxits_inloop,
    maxits_final,
    bounds,
    bestatom_inits,
    bestatom_inits_replacement,
    save_history,
    out_dic
)

```

CL-OMP(R)アルゴリズム。パラメータと重みのペア `(θ, α)` を返し、理想的には `‖Sketch(θ,α)-s‖₂` を最小化します。スケッチは `A` に従って計算されます。ここで、`θ` は `prmtype.p` × `k` のパラメータ行列で、`α` は関連する重みの長さ `k` のベクトルです。

オプションのパラメータ：

  * `replacement`: 繰り返し回数が `k` の代わりに `2k` に設定されます。`k` 回目の繰り返しの後、最適化は `k`+1 の原子に対して行われ、最良の `k` が保持されます。
  * `init_method`: 新しい原子を選択するための方法（デフォルト: :uniform, :randn, :atzero）。オプション :uniform では境界を提供する必要があります。サポートされる引数はパラメータのタイプによって変わる可能性があります。
  * `maxits_inloop`: メインループ内のグローバル最適化の最大繰り返し回数（Int、デフォルト: `300`）。
  * `maxits_final`: 最後のグローバル最適化の最大繰り返し回数（Int、デフォルト: `3000`）。
  * `bounds`: 最適化パラメータの下限、上限のタプル（デフォルト: `(-Inf,Inf)`）。各境界はスカラーまたは `prmtype` に提供された次元と一致するベクトルであることができます。最適化パラメータが複数の変数に対応する場合（例: GMMのμとσ）、自動ベクトル化が意味を持たない可能性があるため、ベクトル境界を使用することが推奨されます。
  * `init_bounds`: 新しい原子を探すときに使用される境界。提供されない場合は、初期化にも `bounds` が使用されます。
  * `bestatom_inits`: 最初の `k` ステップで新しい原子を選択する際の初期化試行の数（最良のものが保持される）（Int、デフォルト: `3`）。
  * `bestatom_inits_replacement`: 置換ステップで新しい原子を選択する際の初期化試行の数（最良のものが保持される）（Int、デフォルト: `10`）。
  * `save_history`: Bool（デフォルト: `false`）、`out_dic` を提供する必要があります。
  * `out_dic`: Dict（デフォルト: なし）。提供されると、アルゴリズムに関する情報がこの辞書に保存されます。
  * `weights_update`: `:always, :onceperit, :attheend (デフォルト), :never` のいずれかである必要があります。
  * `weights_update_method`: `:normalize, :project (デフォルト)` のいずれかである必要があります。ここで、`:project` は単体上への射影を意味します。
