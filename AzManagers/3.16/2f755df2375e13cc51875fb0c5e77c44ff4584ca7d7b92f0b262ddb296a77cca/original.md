```
ispreempted,notbefore = preempted([id=myid()|id="instanceid"])
```

Check to see if the machine `id::Int` has received an Azure spot preempt message.  Returns (true, notbefore) if a preempt message is received and (false,"") otherwise.  `notbefore` is the date/time before which the machine is guaranteed to still exist.
