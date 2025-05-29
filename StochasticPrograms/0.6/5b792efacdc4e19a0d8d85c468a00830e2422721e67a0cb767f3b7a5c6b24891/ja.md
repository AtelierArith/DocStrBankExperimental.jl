```
optimize!(stochasticprogram::StochasticProgram; crash::AbstractCrash = Crash.None(), cache::Bool = false; kw...)
```

期待値で`stochasticprogram`を最適化します。まだオプティマイザーが設定されていない場合（[`set_optimizer`](@ref)を参照）、`NoOptimizer`エラーがスローされます。オプションのクラッシュ手順を設定してウォームスタートすることができます。`cache`フラグをtrueに設定すると、成功裏に終了した場合、モデル内のすべての関連属性の解の値をキャッシュしようとします。これにより、将来の`evaluate`呼び出しの後でも、最適解が上書きされることはありません。

## 例

以下は、L字型アルゴリズムを使用して確率プログラム`sp`を解決します。

```julia
set_optimizer(sp, LShaped.Optimizer)
set_optimizer_attribute(sp, MasterOptimizer(), GLPK.Optimizer)
set_optimizer_attribute(sp, SubProblemOptimizer(), GLPK.Optimizer)
optimize!(sp);

# 出力

L-Shaped Gap  時間: 0:00:02 (6回の反復)
  目的:       -855.8333333333358
  ギャップ:             0.0
  カットの数:  8
  反復回数:      6
```

以下は、拡張形式でGLPKを使用して確率プログラム`sp`を解決します。

```julia
using GLPK

set_optimizer(sp, GLPK.Optimizer)
optimize!(sp)

```

参照: [`VRP`](@ref)
