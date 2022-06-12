## How to setup databricks CLI
```
conda install -c conda-forge databricks-cli
#OR
python3 -m venv ~/my_venv_python
source ~/my_venv_python/bin/activate
pip install databricks-cli
```

## Alternatively we can run below commands on Azure CLI
- Open Azure CLI and click Create Storage if prompted

```
databricks configure --token
```

- Enter your workspace URL, with the format https://<instance-name>.cloud.databricks.com.
  - Sample: https://adb-76115208643438.18.azuredatabricks.net
- When prompted, specify the token
  - Sample Token: dapi40cf9366---------7eaaf44e97ac843-2

- Check the configuration on windows:
```
type %USERPROFILE%\.databrickscfg
cat ~/.databrickscfg
```


- List files in DBFS
```
dbfs ls
```


- Put local file ./apple.txt to dbfs:/apple.txt
```
touch apple.txt
echo "My Apple"
dbfs cp ./apple.txt dbfs:/apple.txt
```


- Get dbfs:/apple.txt and save to local file ./apple.txt
```
dbfs cp dbfs:/apple.txt ./apple_2.txt
ls a*
```


- Run various databricks cli commands:
```
databricks jobs list --output JSON
databricks clusters list --output JSON
databricks jobs run-now --job-id 9 --jar-params "[\"20180505\", \"alantest\"]"
databricks workspace ls
```

## Create databricks cluster using CLI
- Create cluster:
```
databricks clusters create --json-file create-cluster.json
```

- Get details of cluster created:
```
databricks clusters get --cluster-name standard-cluster
```
- Delete Cluster
```
databricks clusters delete --cluster-id "0508-080937-43ys6d98"
```

- For more details on Databricks CLI Commands, refer:
  - https://docs.databricks.com/dev-tools/cli/clusters-cli.html
