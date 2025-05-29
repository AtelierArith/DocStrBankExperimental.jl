X線の特性 `z inner-outer` によって `ionized` サブシェルのイオン化に続いて放出されるX線の分数を表します。カスケードのため、`inner` は必ずしも `ionized` と等しくなりません。`ionized` サブシェルは、オージェ、蛍光、またはコスター-クロニッヒ遷移の組み合わせを介して `inner` の価数に遷移することがあります。さまざまな異なる形式は、`ionized` と `inner` の関係、および `outer` についての仮定を行います。

```
fluorescenceyield(ass::AtomicSubShell)::Float64
```

指定されたシェルからの緩和のうち、任意の放射遷移を介して緩和する分数。(`inner`==`ionized`)

```
fluorescenceyield(cxr::CharXRay)
```

`inner(cxr)` のイオン化のうち、1つの経路 `cxr` を介して緩和する分数。`ionized==inner` && outer(cxr)

```
fluorescenceyield(ash::AtomicSubShell, cxr::CharXRay)::Float64
```

`ash` の各イオン化に対して放出される `cxr` X線の分数（平均）。これは `inner`、`outer`、および `ionized` についての仮定を行いません。
