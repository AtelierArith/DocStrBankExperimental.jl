```
mjv_applyPerturbPose(m, d, pert, flg_paused)
```

選択されたボディがモーションキャプチャの場合、d->mocapに摂動位置、クォータニオンを設定し、それ以外の場合はd->qposに設定します。flg_pausedが真で、選択されたボディのサブツリーのルートが自由関節を持つ場合のみ、d->qposを書き込みます。
