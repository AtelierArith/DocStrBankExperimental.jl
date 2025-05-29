```
set_verbose(verbose::Bool=false)
```

ログのためのグローバルな冗長性レベルを設定します。

# 引数

  * `verbose::Bool`: true の場合、冗長なログを有効にします。false の場合、無効にします。デフォルトは false です。

# 例

```julia
set_verbose(true)  # 冗長なログを有効にします
set_verbose(false) # 冗長なログを無効にします
```
