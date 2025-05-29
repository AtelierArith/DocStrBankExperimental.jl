# sr_path

StatisticalRethinkingのsrc/ディレクトリを使用した相対パス。

### データサブディレクトリにアクセスする例

```julia
sr_path("..", "data")
```

プロジェクト、例えばSR2StanPluto.jlやSR2TuringPluto.jlでは、DrWatsonアプローチがより良い選択であることに注意してください。すなわち: `sr_datadir(filename)`
