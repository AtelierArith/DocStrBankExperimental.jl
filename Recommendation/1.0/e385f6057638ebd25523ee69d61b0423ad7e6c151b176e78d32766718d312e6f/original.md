```
get_data_home([data_home=nothing]) -> String
```

Return an absolute path to a directory containing datasets. Create the directory if it does not exist, and `data_home=nothing` defaults to either an environmental variable `JULIA_RECOMMENDATION_DATA` or `~/julia_recommendation_data`.

Reference: [Similar function in scikit-learn](https://github.com/scikit-learn/scikit-learn/blob/7e1e6d09bcc2eaeba98f7e737aac2ac782f0e5f1/sklearn/datasets/_base.py#L34).
