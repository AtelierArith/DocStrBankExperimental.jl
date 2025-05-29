```julia
process_sample(processor, exec_folder, round)

```

ディスクレコーダーを使用して保存されたサンプルを、指定された`round`で処理します。

各サンプルは`processor`関数に渡され、`processor(chain_index, scan_index, sample)`を呼び出すことで処理されます。ここで、`chain_index`はターゲットチェーンのインデックス（古典的なパラレルテンパリングでは、ターゲット温度でのチェーンは1つだけなので、その場合は無視できますが、例えば安定化変分パラレルテンパリングでは非自明になります）、`scan_index`はラウンド内の反復インデックスで、1から始まり、sampleはデシリアライズされたサンプルです。

これは、外側のループで`chain_index`を、内側のループで`scan_index`をループしながら、サンプルを増加順に反復処理します。
