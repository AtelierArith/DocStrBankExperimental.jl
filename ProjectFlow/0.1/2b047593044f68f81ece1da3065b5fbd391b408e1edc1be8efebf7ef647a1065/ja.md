function initiate(p::Project)

これは、他のすべての関数を組み合わせるメイン関数であり、プロジェクトのタイプの値を与えると、関数は初期化子を検証し、新しいプロジェクトを作成するか、既存のプロジェクトをロードします。

# 引数

  * p: プロジェクトのタイプの値

# 例

```
p = Project(
    id="xyz",
    name="My Fancy? *Project1 2 ",
    template="jl",
    profile="default"
)
initiate(p)
```
