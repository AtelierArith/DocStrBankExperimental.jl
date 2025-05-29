```
runscan(f, scan)
```

関数 `f` を `scan::Scan` によって定義された引数でスキャン内で実行します。関数 `f` は `f(scanidx, args...)` というシグネチャを持つ必要があり、`args` の長さはスキャンされる変数の数に対応します。`do` ブロック構文と共に使用できます。

実行されるスキャンポイントの正確なサブセットと順序は `scan.exec` に依存します。詳細は [`Scan`](@ref) を参照してください。

# 例

```
scan = Scan("scan_example"; energy=collect(range(5e-6, 200e-6; length=64)))
runscan(scan) do scanidx, energyi
    prop_capillary(125e-6, 3, :He, 0.8; λ0=800e-9, τfwhm=10e-15, energy=energyi)
end
```
