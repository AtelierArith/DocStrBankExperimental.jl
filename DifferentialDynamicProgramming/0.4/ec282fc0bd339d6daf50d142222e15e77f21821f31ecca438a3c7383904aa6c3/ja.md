`0.5*x'*H*x + x'*g` を最小化する  s.t. lower<=x<=upper

入力:      `H`            - 正定値行列   (n * n)      `g`            - バイアスベクトル                (n)      `lower`        - 下限               (n)      `upper`        - 上限               (n)

オプション入力:      `x0`           - 初期状態              (n)      `options`      - 以下を参照                  (7)

出力:      `x`            - 解                   (n)      `result`       - 結果のタイプ (大まかに言うと、高い方が良い、以下を参照)      `Hfree`        - サブスペースのコレスキー因子   (n*free * n*free)      `free`         - 自由次元の集合     (n)
