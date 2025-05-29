```
addprocs_lsf(np::Integer;
             bsub_flags::Cmd=``,
             bpeek_flags::Cmd=`-f`,
             ssh_cmd::Cmd=``,
             bsub_cmd::Cmd=`bsub`,
             bpeek_cmd::Cmd=`bpeek`,
             retry_delays=ExponentialBackOff(n=10,
                                             first_delay=1, max_delay=512,
                                             factor=2),
             throttle::Integer=np,
             params...) =
```

Launch `np` workers on a cluster managed by IBM's Platform Load Sharing Facility.  `bsub_flags` can be used to pass flags to `bsub` that are specific to your cluster or workflow needs.  `ssh_cmd` can be used to launch workers from other than the cluster head node (e.g. your personal workstation). `retry_delays` is a vector of numbers specifying in seconds how long to repeatedly wait for a worker to start.  `throttle` specifies how many workers to launch at once. Having `-f` in bpeek flags (which is the default) will let stdout of workers to be displayed on master too.

# Examples

```
addprocs_lsf(1000; ssh_cmd=`ssh login`, throttle=10)
```
