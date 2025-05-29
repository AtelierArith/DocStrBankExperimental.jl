```
setoption(options)
```

ランタイムでトレースオプションを設定します。optionsパラメータは、ユーザーのニーズに応じて以下のオプションのビット単位のORの組み合わせである必要があります：

  * EXTRAE*CALLER*OPTION MPIルーチンの各エントリまたは出口ポイントで呼び出し元情報をダンプします。呼び出し元レベルはXMLで設定する必要があります。
  * `EXTRAE_HWC_OPTION` ハードウェアカウンタ収集を有効にします。
  * `EXTRAE_MPI_OPTION` MPI呼び出しのトレースを有効にします。
  * `EXTRAE_MPI_HWC_OPTION` MPIルーチンでのハードウェアカウンタ収集を有効にします。
  * `EXTRAE_OMP_OPTION` OpenMPランタイムまたはアウトラインルーチンのトレースを有効にします。
  * `EXTRAE_OMP_HWC_OPTION` OpenMPランタイムまたはアウトラインルーチンでのハードウェアカウンタ収集を有効にします。
  * `EXTRAE_UF_HWC_OPTION` ユーザー関数でのハードウェアカウンタ収集を有効にします。
