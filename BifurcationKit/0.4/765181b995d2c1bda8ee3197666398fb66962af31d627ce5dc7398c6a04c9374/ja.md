```julia
bifurcationdiagram!(
    prob,
    node,
    maxlevel,
    options;
    code,
    halfbranch,
    verbosediagram,
    kwargs...
)

```

[`bifurcationdiagram`](@ref)と似ていますが、以前に計算された`node`を渡して、そこから分岐した枝をさらに計算します。通常、以前に計算された分岐`diagram`から`node = get_branch(diagram, code)`と一緒に使用されます。

# 引数

  * `node::BifDiagNode` 分岐図のノード
  * `maxlevel = 1` 必要な最大再帰レベル。
  * `options = (x, p, level; k...) -> contparams` この関数は、分岐`level`に応じて[`continuation`](@ref)オプションを変更することを可能にします。引数`x, p`は、現在の解を示します。`F(x, p)=0`。

# オプションの引数

  * `code = "0"` 反復を表示するために使用されるコード
  * `usedeflation = false`
  * `halfbranch = false` ピッチフォーク/トランスクリティカル分岐の場合、枝の半分のみを計算します。対称性がある場合に便利です。
  * `verbosediagram` 分岐図に特有の冗長情報。枝が計算される際の情報を印刷します。
  * `kwargs` [`continuation`](@ref)と同様のオプションの引数ですが、[Continuation](https://bifurcationkit.github.io/BifurcationKitDocs.jl/dev/library/#Continuation-1)にリストされている異なるバージョンのためのものでもあります。
