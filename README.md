A docker project for building a termsuite-istex docker image including its 3rd-party dependencies and `IstexLauncher` (terminology extraction over an Istex corpus).

# Building TermSuite docker image

1. Clone this docker project:

```
$ git clone https://github.com/termsuite/termsuite-istex-docker.git
```

2. Build the docker image:

```
$ cd termsuite-istex-docker
$ bin/build
```

This will build the docker image `termsuite-istex:X.Y.Z` where `X.Y.Z` is the version of TermSuite. The version of termsuite-istex (and of the docker image to build) can be set or changed in the `Dockerfile`, within the instruction `ENV`:

```
ENV \
  TT_VERSION=3.2.1 \
  TERMSUITE_ISTEX_VERSION=1.1.2 \
```

# Running

Once the image is built you can run IstexLauncher tools with `bin/termsuite-istex`.

```
$ bin/termsuite-istex OPTIONS
```

Where `OPTIONS` are the options you need to run the terminology extraction,
 **except the tagger home option `-t`**, which is no more required here because
 the tagger is installed inside the docker image.

See [TermSuite' Istex launcher](https://github.com/termsuite/termsuite-istex/) to get documentation on available options.

You can also get information by appending `--help`:

```
$ bin/termsuite-istex --help
```

# Examples

The command line below runs terminology extraction on the istex documents `F697EDBD85006E482CD1AC91DE9D40F6C629727A` and `15101397F055B3A872D495F7405D0A3F3E195E0F` with language `en` and outputs the terminology to `istex-termino.tsv`.

```
bin/termsuite-istex -l en --tsv ./istex-termino.tsv --doc-id F697EDBD85006E482CD1AC91DE9D40F6C629727A,15101397F055B3A872D495F7405D0A3F3E195E0F
```
