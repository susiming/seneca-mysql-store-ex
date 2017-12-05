# seneca-mysql-store-ex
seneca-mysql-store 扩展

安装

    $ npm install seneca-mysql-store-ex

介绍

    seneca-mysql-store 的扩展
    1.list查询增加了like操作
    2.增加了类似开源项目thinkjs中model操作
    
1.0.4
    BUG:too many connections
    
1.0.2
    去除load和list返回都含有 entity$ 字段，泄露实体（表）名称

1.0.1

    引入 node-mysql-promise (https://github.com/ffttpp/node-mysql-promise)

    使用示例

        module.exports = function (options) {
            this.add('role:sys,method:list,model:admin', function (msg, respond) {
                var model = this.ThinkMySQL$()
                //SELECT * FROM table;
                model.table('admin').select().then(function (data) {
                    respond(null, data)
                }).catch(function (e) {
                    console.log(e);
                    respond(null, null)
                });
            })
        }

    详细使用说明见：https://github.com/ffttpp/node-mysql-promise

1.0.0

    list$查询操作增加:

    like$: .list$({ f1: { like$: v1 } }) 支持like模糊查询