```
fits_verify_chksum(f::FITSFile)
```

データとHDUのチェックサムが保存された値と一致するかどうかを確認します。データとHDUのチェックサムの状態を示す`CFITSIO.ChecksumVerificationStatus`値のタプルを返します。いずれかの値に対して、`MISSING`の状態は対応するキーワードが存在しないことを示し、`MISMATCH`の状態はキーワードが存在するが値が不正であることを示します。最後に、`VERIFIED`の値はチェックサムが正常に検証されたことを示します。
