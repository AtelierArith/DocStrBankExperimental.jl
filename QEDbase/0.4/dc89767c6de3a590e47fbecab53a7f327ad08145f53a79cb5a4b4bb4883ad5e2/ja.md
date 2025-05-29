```
phase_space_dimension(proc, model, layout::AbstractPhaseSpaceLayout)::Int
```

この関数は、位相空間レイアウトインターフェースのために実装する必要があります。指定された `layout` 内の与えられたプロセスとモデルに対して、位相空間の次元、すなわち座標の数を返します。

位相空間の次元は、散乱プロセスにおける粒子の系を記述するために必要な独立した座標の数を決定する重要な量です。これは、関与する粒子の数と使用される特定の相互作用モデルに依存します。

## 引数

  * `proc`: 散乱プロセスの定義で、[`AbstractProcessDefinition`](@ref) のサブタイプです。
  * `model`: 物理モデルで、[`AbstractModelDefinition`](@ref) のサブタイプです。
  * `layout`: 特定の位相空間レイアウトで、[`AbstractInPhaseSpaceLayout`](@ref) または [`AbstractOutPhaseSpaceLayout`](@ref) のいずれかです。

## 戻り値

  * 独立した位相空間座標の数を表す整数。

!!! note
    この関数はコンパイル時定数を返す必要があります。すなわち、関数呼び出しの型情報からのみ推測できる数です。これが当てはまらない場合、`build_momenta` や他の派生関数が非常に遅くなる可能性があります。

