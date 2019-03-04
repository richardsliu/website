This tool is cloned from https://github.com/ahmetb/gen-crd-api-reference-docs.

Prerequisites:
* Go 1.11+
* Clones of the source API repositories

Usage:

1. Build the tool from this directory: 
```
export GEN_DOCS=$(pwd)
GO111MODULE=on go build
```

1. Set up the target HTML content path, for example:
```
export CONTENT_DIR=$(pwd)/../../content/docs/references/tfjob/v1beta2
```

1. Go to the directory where your API repository is cloned. The tool assumes that you are at the root of the repo, and that your GOPATH is set properly. For example:
```
cd $GOPATH/src/github.com/kubeflow/tf-operator/
```

1. Run the tool to generate the API html files at the desired locations. For example:
```
$GEN_DOCS/gen-crd-api-reference-docs -config $GEN_DOCS/kubeflow-config.json -template-dir $GEN_DOCS/template -api-dir "github.com/kubeflow/tf-operator/pkg/apis/common/v1beta2" -out-file $CONTENT_DIR/common.html

$GEN_DOCS/gen-crd-api-reference-docs -config $GEN_DOCS/kubeflow-config.json -template-dir $GEN_DOCS/template -api-dir "github.com/kubeflow/tf-operator/pkg/apis/tensorflow/v1beta2" -out-file $CONTENT_DIR/tensorflow.html
```

1. Open a PR to submit the changes to the website.
