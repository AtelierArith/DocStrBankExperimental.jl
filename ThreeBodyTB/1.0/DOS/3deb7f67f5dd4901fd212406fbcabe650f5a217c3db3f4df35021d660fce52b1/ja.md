```
function dos_realspace(tbc; direction=3, grid=missing, smearing=0.005, npts=missing, do_display=true, use_sym=false, energy_grid=100, width=missing, energy_lims=missing, scissors_shift=0.0, scissors_shift_atoms=[])
```

原子と空間的に解像度のあるDOSスタイルのプロットを作成します。`direction=1,2,3`（格子ベクトル1,2,3）に沿って、原子がプロットされ、DOS振幅を示すために透明度が使用されます。試してみてください。インターフェースにとって潜在的に有用です。使用例: `c = makecrys([8.0 0 0; 0 8.0 0; 0 0 10.0], [0 0 0; 0 0 0.5], [:Li, :Cl]) #準1次元LiClチェーン` `en, tbc, flag = scf_energy(c*[1,1,10])                                   #10ユニットセル` `dos_realspace(tbc, direction=3)`

プロットパラメータを調整するには、`energy_grid`と`width`を調整してください。特定の原子に対するエネルギー単位のシザーズシフトは、必要に応じてバンドギャップを開くためにシザーズシフトを追加します。
