```
loadnmr(filename, experimentfolder=nothing)
```

NMRデータを読み込むためのメイン関数です。`experimentfolder`は、メタデータの識別のために実験ディレクトリへのパスを含みます。ファイル名が実験内に直接存在しない場合に使用します。

`NMRData`構造体を返すか、問題がある場合は`NMRToolsError`をスローします。

# 例

nmrPipeのインポート:

```julia
loadnmr("exampledata/1D_1H/1/test.ft1");
loadnmr("exampledata/1D_19F/1/test.ft1");
loadnmr("exampledata/2D_HN/1/test.ft2");
loadnmr("exampledata/pseudo2D_XSTE/1/test.ft1");
loadnmr("exampledata/pseudo3D_HN_R2/1/ft/test%03d.ft2");
```

Bruker pdataのインポート:

```julia
loadnmr("exampledata/1D_19F/1");
loadnmr("exampledata/1D_19F/1/");
loadnmr("exampledata/1D_19F/1/pdata/1");
loadnmr("exampledata/1D_19F/1/pdata/1/");
```

ucsf (Sparky)のインポート:

```julia
loadnmr("exampledata/2D_HN/1/hmqc.ucsf");
loadnmr("exampledata/1D_19F/1/");
loadnmr("exampledata/1D_19F/1/pdata/1");
loadnmr("exampledata/1D_19F/1/pdata/1/");
```
