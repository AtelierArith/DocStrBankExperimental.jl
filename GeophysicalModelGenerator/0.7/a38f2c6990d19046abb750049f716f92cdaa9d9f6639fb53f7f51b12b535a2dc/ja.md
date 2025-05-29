```
nProcX,nProcY,nProcZ, xc,yc,zc, nNodeX,nNodeY,nNodeZ = get_processor_partitioning(filename; is64bit=false)
```

LaMEMプロセッサパーティショニングファイルを読み取り、マーカーファイルを作成するために使用し、並列レイアウトを返します。デフォルトでは、これは32ビットのPETScインストール用に行われ、実際に64ビットバージョンを使用すると失敗します。
