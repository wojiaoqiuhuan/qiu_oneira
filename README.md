# ONEIRA 烘焙连锁工作台 V5

V5 是可部署使用版：Node.js + Express + PostgreSQL + Socket.IO。

## 1. 本地运行

需要 Node.js 20+ 与 PostgreSQL。

```bash
npm install
```

创建 `.env`：

```env
DATABASE_URL=postgresql://USER:PASSWORD@HOST:5432/oneira
JWT_SECRET=请替换为随机长字符串
NODE_ENV=production
PORT=3000
```

然后：

```bash
npm start
```

打开 `http://localhost:3000`。

首次启动会自动创建数据库表并写入演示数据。

## 2. 演示账号

店长：咸阳店 / 李店长 / BAKE2024

运营：运营 / oneira2026

管理员：管理员 / oneira2026

正式上线前务必修改密码与 JWT_SECRET。

## 3. V5 功能

- Apple 风格高端 UI，PC / 手机响应式
- 店长：日报直接填写，不再上传文件
- 管理员：可新增、修改、启停日报字段；字段实时同步到店长端
- 日报覆盖：同一门店同一天唯一，覆盖时保留 version 版本号
- 目标月历：月目标、每日目标、实际完成、完成率
- 月目标：按天平均 / 周末权重 / 自定义每日目标
- 自定义目标严格校验每日之和等于月目标
- 日报营业额自动回填对应日期任务
- 运营反馈处理，结果同步店长
- 门店管理、员工姓名管理、口令修改、门店归档
- 管理员操作日志
- CSV 月度日报导出
- Socket.IO 秒级变更广播
- PostgreSQL 持久化

## 4. 正式部署

推荐 Render / Railway 等 Node Web Service + PostgreSQL。

Build：`npm install`

Start：`npm start`

环境变量：`DATABASE_URL`、`JWT_SECRET`、`NODE_ENV=production`

注意：正式环境应限制 CORS 来源、启用 HTTPS，并把管理员初始密码修改掉。

## 5. 数据关系

日报 -> KPI -> 每日任务实际完成 -> 月历完成率

反馈 -> 运营处理 -> 店长可见

管理员日报模板 -> 店长日报表单

门店口令 / 员工姓名 -> 登录与操作追溯
