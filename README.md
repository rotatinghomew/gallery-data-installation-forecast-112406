# 联合数字展工程交接和付款资料

以下台账为合成数据，不涉及真实访客、供应商或展馆。CSV 采用 UTF-8，首行为字段名，空字段代表源资料未给出。标识仅在字段明示的实体范围内使用。`data/agreements.json` 是当期业务方提供的运营资料，`data/formats.json` 记录文件列顺序和确定的外键引用。

- `data/projects.csv` 记录项目的拟订期、共享施工班组及开厅约定。列为 `project`、`venue`、`vendor`、`shared_team`、`decide`、`promised`、`state`。
- `data/milestones.csv` 记录部件经费、执行班组、器材批和最早计划日。列为 `item`、`project`、`kind`、`performer`、`claim_cent`、`crew_need`、`lot`、`planned_day`。
- `data/links.csv` 记录交场合同中的验收依赖与关联。列为 `predecessor`、`successor`、`kind`、`source`。
- `data/acceptance.csv` 记录历次业务方的实际报工、验收与撤销回执，fraction 为百分值。列为 `receipt`、`item`、`state`、`day`、`received`、`fraction`、`actor`。
- `data/contracts.csv` 记录付款义务涵盖的馆及工程单元，列表以竖线分隔。列为 `bill`、`projects`、`items`、`method`、`expires`、`deposit_cent`。
- `data/payments.csv` 记录财务已实付或待付款，空 item 是合同级预付款。列为 `receipt`、`bill`、`item`、`date`、`amount_cent`、`state`。
- `data/crew_windows.csv` 记录调度确认的连续日期区间及最大并行占用；空回执时可立即使用。列为 `crew`、`first`、`last`、`simultaneous_capacity`、`available_after_receipt`。
- `data/options.csv` 记录同一联展期的对比安排。两个方案可以共享人手，shares_crew 指同队不能同时承接的重叠资源。列为 `plan`、`projects`、`open_day`、`kind`、`main_items`、`shares_crew`、`approval`。

使用 Python 3.11，无第三方依赖。用 `python3 -m unittest discover -s tests -v` 核对文件的可读性、列结构和确定引用，源文件保持只读。
