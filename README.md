This repository reproduces steep's random error. The error actually depends on environment.
Until Ruby 2.8, Pathname.glob's order depends on environment.

https://github.com/soutaro/steep/blob/16da96f069b7d0ba28d833301fc7510fcdfe2824/lib/steep/project/file_loader.rb#L17-L21


So this code returns paths randomly.

As a result, steep randomly reports errors when extensions are defined in two files.


# How to reproduce

This repository has two rbs files, that are a.rbs and b.rbs.
`steep check` on this repository may be success, or reports an error. But if swap the rbs files, the result will be also swapped.

