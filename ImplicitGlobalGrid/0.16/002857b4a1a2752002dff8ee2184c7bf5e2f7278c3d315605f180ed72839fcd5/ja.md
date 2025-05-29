```
update_halo!(A)
update_halo!(A...)
```

!!! note "Advanced"
    ```
    update_halo!(A, B, (A=C, halowidths=..., (A=D, halowidths=...), ...)
    ```


与えられたGPU/CPU配列のハローを更新します。

# 一般的な使用例:

```
update_halo!(A)                                # 配列Aのハローを更新します。
update_halo!(A, B, C)                          # 配列A、B、Cのハローを更新します。
update_halo!(A, B, (A=C, halowidths=(2,2,2)))  # 配列A、B、Cのハローを更新し、Cのためにデフォルト以外のhalowidthを定義します。
```

!!! note "Performance note"
    パフォーマンスを向上させるために、`update_halo!`の後続の呼び出しを単一の呼び出しにグループ化します（追加のパイプライン処理を可能にします）。


!!! note "Performance note"
    システムがCUDA対応MPI（Nvidia GPU用）またはROCm対応MPI（AMD GPU用）をサポートしている場合、次の環境変数のいずれかを設定することでImplicitGlobalGridを有効にできます（`init_global_grid`の呼び出しの前に設定する必要があります）：

    ```shell
    shell> export IGG_CUDAAWARE_MPI=1
    ```

    ```shell
    shell> export IGG_ROCMAWARE_MPI=1
    ```

