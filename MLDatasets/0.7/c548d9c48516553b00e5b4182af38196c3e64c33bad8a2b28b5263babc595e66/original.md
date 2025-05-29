```
Reddit(; full=true, dir=nothing)
```

The Reddit dataset was introduced in Ref [1]. It is a graph dataset of Reddit posts made in the month of September, 2014. The dataset contains a single post-to-post graph, connecting posts if the same user comments on both.  The node label in this case is one of the 41 communities, or “subreddit”s, that a post belongs to.   This dataset contains 232,965 posts. The first 20 days are used for training and the remaining days for testing (with 30% used for validation). Each node is represented by a 602 word vector.

Use `full=false` to load only a subsample of the dataset.

# References

[1]: [Inductive Representation Learning on Large Graphs](https://arxiv.org/abs/1706.02216)

[2]: [Benchmarks on the Reddit Dataset](https://paperswithcode.com/dataset/reddit)
