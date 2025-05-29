```
@∀ x ∈ X ステートメント
@∀ x in X ステートメント
@∀ x = X ステートメント
```

`X` のすべての `x` に対して `ステートメント` を展開します。

# 引数

  * `x`: `ステートメント` を展開するための変数の名前。
  * `X`: `x` が展開される名前の集合または値の範囲。
  * `ステートメント`: 展開されるステートメント。

# 例

```
@∀ i ∈ (x,z) @all(C.i) = @all(A.i) + @all(B.i)                     # Equivalent to: @all(C.x) = @all(A.x) + @all(B.x)
                                                                   #                @all(C.z) = @all(A.z) + @all(B.z)

@∀ i ∈ (y,z) C.i[ix,iy,iz] = A.i[ix,iy,iz] + B.i[ix,iy,iz]         # Equivalent to: C.y[ix,iy,iz] = A.y[ix,iy,iz] + B.y[ix,iy,iz]
                                                                   #                C.z[ix,iy,iz] = A.z[ix,iy,iz] + B.z[ix,iy,iz]

@∀ (ij,i,j) ∈ ((xy,x,y), (xz,x,z), (yz,y,z)) @all(C.ij) = @all(A.i) + @all(B.j)  # Equivalent to: @all(C.xy) = @all(A.x) + @all(B.y)
                                                                                 #                @all(C.xz) = @all(A.x) + @all(B.z)
                                                                                 #                @all(C.yz) = @all(A.y) + @all(B.z)

@∀ i ∈ 1:N @all(C[i]) = @all(A[i]) + @all(B[i])                    # Equivalent to: @all(C[1]) = @all(A[1]) + @all(B[1])
                                                                   #                @all(C[2]) = @all(A[2]) + @all(B[2])
                                                                   #                ...
                                                                   #                @all(C[N]) = @all(A[N]) + @all(B[N])

@∀ i ∈ 1:N C[i][ix,iy,iz] = A[i][ix,iy,iz] + B[i][ix,iy,iz]        # Equivalent to: C[1][ix,iy,iz] = A[1][ix,iy,iz] + B[1][ix,iy,iz]
                                                                   #                C[2][ix,iy,iz] = A[2][ix,iy,iz] + B[2][ix,iy,iz]
                                                                   #                ...
                                                                   #                C[N][ix,iy,iz] = A[N][ix,iy,iz] + B[N][ix,iy,iz]
```

!!! note "パフォーマンスノート"
    特定の方程式の集合に対して簡潔な表記法を可能にするだけでなく、`@∀` マクロは計算カーネル内の小さな値の範囲に対する for ループを置き換えるように設計されており、しばしばより良いパフォーマンスをもたらします。


!!! note "記号 ∀"
    記号 `∀` は、例えば、Julia REPL や VSCode で `orall` と入力し、`TAB` を押すことで取得できます。

