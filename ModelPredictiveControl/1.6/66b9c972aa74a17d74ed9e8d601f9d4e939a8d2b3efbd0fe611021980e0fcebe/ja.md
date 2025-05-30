```
LinModel(sys::StateSpace[, Ts]; i_u=1:size(sys,2), i_d=Int[])
```

状態空間モデル `sys` からサンプリング時間 `Ts`（秒単位）で線形モデルを構築します。

システム `sys` は連続時間または離散時間であり（後者の場合、`Ts` は省略可能です）、連続動力学の場合、その状態空間方程式は次のようになります（離散ケースは拡張ヘルプに記載）：

$$
\begin{aligned}
    \mathbf{ẋ}(t) &= \mathbf{A x}(t) + \mathbf{B z}(t) \\
    \mathbf{y}(t) &= \mathbf{C x}(t) + \mathbf{D z}(t)
\end{aligned}
$$

状態ベクトル $\mathbf{x}$ と出力ベクトル $\mathbf{y}$ があります。ベクトル $\mathbf{z}$ は操作された入力 $\mathbf{u}$ と測定された外乱 $\mathbf{d}$ で構成され、順序は問われません。`i_u` は操作された $\mathbf{z}$ のインデックスを提供し、`i_d` は測定された外乱を提供します。コンストラクタは連続システムを自動的に離散化し、`Ts ≠ sys.Ts` の場合は離散システムを再サンプリングし、新しいバランスと最小状態空間実現を計算し、$\mathbf{z}$ の項を2つの部分に分けます（詳細は拡張ヘルプに記載）。ドキュメントの残りの部分は、すべてのシステムがこの形式に最終的に到達するため、離散モデルを前提としています。

[`ss`](@extref ControlSystemsBase.ss) も参照してください。

# 例

```jldoctest
julia> model1 = LinModel(ss(-0.1, 1.0, 1.0, 0), 2.0) # 連続時間 StateSpace
LinModel with a sample time Ts = 2.0 s and:
 1 manipulated inputs u
 1 states x
 1 outputs y
 0 measured disturbances d

julia> model2 = LinModel(ss(0.4, 0.2, 0.3, 0, 0.1)) # 離散時間 StateSpace
LinModel with a sample time Ts = 0.1 s and:
 1 manipulated inputs u
 1 states x
 1 outputs y
 0 measured disturbances d
```

# 拡張ヘルプ

!!! details "拡張ヘルプ"
    状態空間方程式は、`sys` が離散時間の場合も似ています：

    $$
    \begin{aligned}
        \mathbf{x}(k+1) &=  \mathbf{A x}(k) + \mathbf{B z}(k) \\
        \mathbf{y}(k)   &=  \mathbf{C x}(k) + \mathbf{D z}(k)
    \end{aligned}
    $$

    連続動力学は、操作された入力に対しては [`c2d`](@extref ControlSystemsBase.c2d) と `:zoh` を使用して内部的に離散化され、測定された外乱に対しては `:tustin` が使用されます。最後に、`sys` が離散で提供された引数 `Ts ≠ sys.Ts` の場合、システムは前述の離散化手法を使用して再サンプリングされます。

    コンストラクタは、制御可能性/可観測性のために [`minreal`](@extref ControlSystemsBase.minreal) を使用してシステムを最小かつバランスの取れた実現に変換することに注意してください。その結果、最終的な状態空間表現は、`sys` で提供されたものとは異なる可能性があります。また、ゼロオーダーホールドのために、より実用的な形式に変換されます（$\mathbf{D_u=0}$）：

    $$
    \begin{aligned}
        \mathbf{x}(k+1) &=  \mathbf{A x}(k) + \mathbf{B_u u}(k) + \mathbf{B_d d}(k) \\
        \mathbf{y}(k)   &=  \mathbf{C x}(k) + \mathbf{D_d d}(k)
    \end{aligned}
    $$

    特定の状態空間表現を強制するには、構文 [`LinModel{NT}(A, Bu, C, Bd, Dd, Ts)`](@ref) を使用してください。


```
