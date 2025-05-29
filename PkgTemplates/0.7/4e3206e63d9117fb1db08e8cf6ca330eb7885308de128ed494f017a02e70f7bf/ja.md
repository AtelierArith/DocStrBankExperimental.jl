```
Tests(;
    file="~/.julia/packages/PkgTemplates/MepaC/templates/test/runtests.jlt",
    project=false,
    aqua=false,
    aqua_kwargs=NamedTuple(),
    jet=false,
)
```

パッケージのテストを設定します。

## キーワード引数

  * `file::AbstractString`: `runtests.jl` のテンプレートファイル。
  * `project::Bool`: テスト用に新しいプロジェクトを作成するかどうか (`test/Project.toml`)。詳細については [Pkg ドキュメント](https://julialang.github.io/Pkg.jl/v1/creating-packages/#Test-specific-dependencies-in-Julia-1.2-and-above-1) を参照してください。
  * `aqua::Bool`: [Aqua.jl](https://github.com/JuliaTesting/Aqua.jl) を使用して品質テストを追加するかどうかを制御します。
  * `aqua_kwargs::NamedTuple`: Aqua テストに供給するキーワード引数（多くの人が `ambiguities=false` を使用します）
  * `jet::Bool`: [JET.jl](https://github.com/aviatesk/JET.jl) を使用してリンティングテストを追加するかどうかを制御します（型安定なコードで最も効果的です）

!!! note
    `test/Project.toml` でのテスト依存関係の管理は、Julia 1.2 以降でのみサポートされています。

