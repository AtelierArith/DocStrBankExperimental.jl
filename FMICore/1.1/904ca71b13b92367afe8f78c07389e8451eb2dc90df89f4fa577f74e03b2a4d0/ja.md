ソース: FMISpec3.0, バージョン D5ef1c1: 2.2.9.4. スケジュール実行列挙型は、間隔と intervalCounters 引数の扱いを説明する IntervalQualifiers を定義します。これらは以下の意味を持ちます: fmi3IntervalNotYetKnown - 次の間隔がまだ知られていないカウントダウン非周期クロックに対して返されます。この修飾子の値は、クロックがアクティブであった直後にのみ返され、fmi3GetInterval の以前の呼び出しが fmi3IntervalChanged (または fmi3IntervalUnchanged) を返さなかった場合に限ります。スケジュール実行において、この返り値は対応するモデルパーティションがまだスケジュールできないことを意味します。

fmi3IntervalUnchanged - 以前の fmi3GetInterval の呼び出しが fmi3IntervalChanged で修飾された値を返しており、それ以降変更されていない場合に返されます。スケジュール実行において、これは対応するモデルパーティションがすでにスケジュールされていることを意味します。

fmi3IntervalChanged - このクロックの間隔の値が変更されたことを示すために返されます。以前に返された間隔（もしあれば）は現在の値で上書きされます。新しいクロック間隔は、周期的クロックの間隔が連続するクロックティック間の時間として定義されるのに対し、現在のイベントモードまたはクロック更新モードの時間に対して相対的です。スケジュール実行において、これは対応するモデルパーティションがスケジュールまたは再スケジュールされる必要があることを意味します（以前の fmi3GetInterval の呼び出しが fmi3IntervalChanged を返した場合）。
