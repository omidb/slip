# SLIP-NNN - IO Target

**By: Omid Bakhshandeh**

This document is provided as a template to get you started. Feel free to add, augment,
remove, restructure and otherwise adapt the structure for what you need after cloning it.
Create a fork of this repository and a new feature branch called slip/NNN (where
NNN is the SLIP number).
This document should be then be copied into slip-NNN/slip-NNN.md. You can also use
this slip-NNN directory to hold any supporting documentation, code and tests.

## History

| Date          | Version       |
|---------------|---------------|
| Jun 18th 2015 | Initial Draft |

## Motivation

`scala.io.Source` is one of the most used part of `Scala std`. For many people that are new
to the language and programming IO play an important role.
Scala std doesn't have any support for generating output. Scala programmers use `Java.io`
or `Java.nio` for writing on disk. On the other hand, the incopatibility between Java File
and Scala File makes it hard to have nice Scala code.

Here, I propose `Scala.io.Target` to be added to std. This part of library could implement the
output version `Scala.io.Source`.


### Examples

An example could be something like this:

```scala
def fromFile(file: File, bufferSize: Int)(implicit codec: Codec): BufferedSource

def toFile(file: File, bufferSize: Int)(implicit codec: Codec): BufferedTarget

```
It's important to investigate the parts that are a little bit tricky to implement or even impossible like:

```scala
fromURL(url: URL)(implicit codec: Codec): BufferedSource

toURL(url: URL)(implicit codec: Codec): BufferedTarget // is it possible to start a simple webserver
                                                       //or something like that?
```


## Drawbacks

The only reason that this library shouldn't be implemented is the richness of Java IO library. If this library
is not good enough that people use it and cannot provide all Java.IO functionality like `ByteWriter` or `Channels`,
then implemeting this library could be a waste of time.

## Alternatives
There are some alternatives like `Scalaz` and others, but I think this should be really part of Scala std.