```
textcurve(the_text, start_angle, start_radius, pos;
      # オプションのキーワード引数:
      spiral_ring_step = 0,    # この量だけ外側または内側にステップ
      letter_spacing = 0,      # 文字間のトラッキング/スペース、タイトは(-)、ルーズは(+)
      spiral_in_out_shift = 0, # +の値は外向き、-の値は内向きにスパイラル
      clockwise = true
      )
```

曲線上にテキストの文字列を配置します。スパイラルに内向きまたは外向きにできます。

`start_angle`は+ve x軸に対して相対的で、弧/円は`pos`を中心に`start_radius`の半径で配置されます。
