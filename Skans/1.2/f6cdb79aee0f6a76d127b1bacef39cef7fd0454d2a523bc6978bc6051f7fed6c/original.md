```
skan!(repo::Repo, pages::Vector{<:Page}; notify=true) -> Vector{PageScan}
```

Compare the `pages` to the stored state in `repo`. Return a vector of changed `pages` and update the repo for each changed page. When no pages changed, the vector is empty.
