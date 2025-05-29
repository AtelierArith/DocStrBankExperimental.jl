```
show_workflow(pnet::Workflow_PetriNet)
```

指定されたペトリネットオブジェクトをSVG文字列に変換し、画面にHTMLとして表示します。この機能は、REPLではなく、IJulia.jlやPluto.jlのような環境内で使用することを意図しています。

# 引数

  * `pnet::Workflow_PetriNet`: 可視化するワークフローを説明するペトリネットオブジェクト
