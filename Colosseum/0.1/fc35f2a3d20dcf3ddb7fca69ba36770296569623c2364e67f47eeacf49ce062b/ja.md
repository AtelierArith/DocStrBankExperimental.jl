環境内の太陽の位置を制御する

太陽の位置は、引数で指定された日時の設定における`OriginGeopoint`に指定された座標を使用して計算されます。文字列が空の場合は、現在の日付と時刻が使用されます。

Args:     is*enabled (bool) 時間帯効果を有効にするにはtrue、元の位置にリセットするにはfalse     start*datetime (str, optional) %Y-%m-%d %H:%M:%S形式の日付と時刻、例: `2018-02-12 15:20:00`     is*start*datetime*dst (bool, optional) 夏時間に調整するにはtrue     celestial*clock*speed (float, optional) 天体時計をシミュレーション時計よりも速く||遅く実行する                                             例: 値100は、シミュレーション時計の1秒ごとに太陽の位置が100秒進むことを意味します                                             そのため、太陽は空の中で非常に速く移動します     update*interval*secs (float, optional) 太陽の位置を更新する間隔     move*sun (bool, optional) 太陽を移動させるかどうか
