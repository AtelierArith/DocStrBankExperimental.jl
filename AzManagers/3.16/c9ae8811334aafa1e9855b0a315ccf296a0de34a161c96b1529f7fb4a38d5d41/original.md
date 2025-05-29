```
addproc(template[; name="", basename="cbox", subscriptionid="myid", resourcegroup="mygroup", nretry=10, verbose=0, session=AzSession(;lazy=true), sigimagename="", sigimageversion="", imagename="", detachedservice=true])
```

Create a VM, and returns a named tuple `(name,ip,resourcegrup,subscriptionid)` where `name` is the name of the VM, and `ip` is the ip address of the VM. `resourcegroup` and `subscriptionid` denote where the VM resides on Azure.

# Parameters

  * `name=""` name for the VM.  If it is not an empty string, then the next paramter (`basename`) is ignored
  * `basename="cbox"` base name for the VM, we append a random suffix to ensure uniqueness
  * `subscriptionid=template["subscriptionid"]` if exists, or `AzManagers._manifest["subscriptionid"]` otherwise.
  * `resourcegroup=template["resourcegroup"]` if exists, or `AzManagers._manifest["resourcegroup"]` otherwise.
  * `session=AzSession(;lazy=true)` Session used for OAuth2 authentication
  * `sigimagename=""` Azure shared image gallery image to use for the VM (defaults to the template's image)
  * `sigimageversion=""` Azure shared image gallery image version to use for the VM (defaults to latest)
  * `imagename=""` Azure image name used as an alternative to `sigimagename` and `sigimageversion` (used for development work)
  * `osdisksize=60` Disk size of the OS disk in GB
  * `customenv=false` If true, then send the current project environment to the workers where it will be instantiated.
  * `nretry=10` Max retries for re-tryable REST call failures
  * `verbose=0` Verbosity flag passes to HTTP.jl methods
  * `show_quota=false` after various operation, show the "x-ms-rate-remaining-resource" response header.  Useful for debugging/understanding Azure quota's.
  * `julia_num_threads="$(Threads.nthreads(),$(Threads.nthreads(:interactive))"` set the number of julia threads for the workers.[1]
  * `omp_num_threads = get(ENV, "OMP_NUM_THREADS", 1)` set `OMP_NUM_THREADS` environment variable before starting the detached process
  * `exename="$(Sys.BINDIR)/julia"` name of the julia executable.
  * `env=Dict()` Dictionary of environemnt variables that will be exported before starting the detached process
  * `detachedservice=true` start the detached service allowing for RESTful remote code execution
  * `use_lvm=false` For SKUs that have 1 or more nvme disks, combines all disks as a single mount point /scratch vs /scratch, /scratch1, /scratch2, etc..

# Notes

[1] Interactive threads are supported beginning in version 1.9 of Julia.  For earlier versions, the default for `julia_num_threads` is `Threads.nthreads()`.
