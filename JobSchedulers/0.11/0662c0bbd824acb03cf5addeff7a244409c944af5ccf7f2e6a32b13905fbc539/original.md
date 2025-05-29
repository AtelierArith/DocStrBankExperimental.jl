```
job_query_by_id(id::Integer)
```

Search job by `job.id` in the queue.

Return `job::Job` if found, `nothing` if not found.
